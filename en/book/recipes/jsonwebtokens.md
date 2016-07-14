## JSON Web Tokens

JSON web tokens (JWT) provide a way to publish a set of *claims* (an array of data) as a text string,
and a way to verify these claims have not been tampered with when that string is processed at a
later time.

For detailed information on JWT, please refer to these resources:

* [jwt.io](https://jwt.io/)
* [RFC7519](https://tools.ietf.org/html/rfc7519)

The [Xmf\Jwt namespace](../jwt/README.md) reference section details the JWT support provided in XMF.

### Why do we need JWT?

In practical terms, JWT allows a script to send information from a server to a client, and then have
that information returned from the client, and be confident the information is unchanged. This is
accomplished by signing the token with a secret key. Note that the signing is for protection against
tampering or corruption, not for encryption. The data in a JWT can be viewed easily. It
is only Base64 encoded for 7 bit path safety in transit.

One common use of a JWT is as stateless authentication tokens.

A practical use case in XOOPS would be as tokens for Ajax processing. XOOPS forms use a
[nonce](https://en.wikipedia.org/wiki/Cryptographic_nonce) token, which is sent to the client, and also
recorded in the user's session on the server. When returned before it expires, it is considered
sufficient evidence that returned form data is the result of user interaction, and not just randomly
submitted from some other source. This provides protection from cross site request forgery (CSRF.)

When using Ajax requests, the *nonce* token is a bad fit. First, the token is sent to the browser one
time, but the browser may initiate many Ajax transactions. While it is possible to check the token without
expiring it, that only complicates the issues. The Ajax interaction is an inherently asynchronous set
of multiple processes. There is no reliable way to refresh a token, as the scripts do not necessarily
follow any order in processing. (The first in, may be the last to complete for example.)

The real issue is there is no way to verify that the token is actually associated with an expected Ajax
process. The token only shows a relationship to the user, not to the process that issued it.
With some care, this weakness could be exploited by something similar to CSRF, but intra-site
instead of cross-site. A token issued in one context is used in another, unintended way. An administrator's
click could be redirected to perform an unintended malicious action. There are additional details to
be completed to establish a viable attack vector, but the stage is set.

### How can we improve that with JSON web tokens?

A token can carry an expiration time (as a UNIX timestamp) in an 'exp' claim. The `Xmf\Jwt\JsonWebToken`
class will verify the 'exp' claim automatically. This allows us to limit the period time that any
asynchronous Ajax interactions can be performed.

We can declare any data as a claim. When creating a token, we can include a claim of what script
created the token. Asserting this claim when validating the token assures us that the token is being
used with the appropriate script.

If needed, we can add additional claims, user id, item id, or whatever else is appropriate.

Issuing the token authorizes interaction with our specific script via Ajax (possibly with further
restriction to specific items) for a limited period of time.

If we send that JWT to the browser, and return it as scripts make Ajax requests, we are sure that token
belongs to the script in use, and that no information in the token has been changed. This is a big step
forward, and it isn't a huge amount of code.

Below is an example script.

If invoked by the browser, it generates a JWT and returns a simple page with one button.

Clicking the button will invoke the same script through Ajax, including the JWT in the headers.

When invoked through Ajax, the script verifies the token from the header. Tokens are only valid
for 2 minutes after being issued. This might be too short for a real application, but it quickly
demonstrates expiration.

This example script can be copied into almost any module directory in XOOPS and run. Watching the
interaction through the javascript console or developer tools demonstrates the full cycle of interaction.

### Ajax protection with JWT

```php
<?php

use Xmf\Jwt\TokenFactory;
use Xmf\Jwt\TokenReader;
use Xmf\Module\Helper;
use Xmf\Request;

include dirname(dirname(__DIR__)) . '/mainfile.php';

// claims we want to assert (verify)
$assertClaims = array('aud' => basename(__FILE__));

if (0 === strcasecmp(Request::getHeader('X-Requested-With', ''), 'XMLHttpRequest')) {
    $xoopsLogger->activated = false;
    $token = TokenReader::fromHeader('test', $assertClaims);
    if (false === $token) {
        http_response_code(401);
        echo "not authorized";
    } else {

        // The real work can happen here!

        http_response_code(200);
        echo $token->data;
    }
    exit;
}

require_once XOOPS_ROOT_PATH . '/header.php';
include __DIR__ . '/include/common.php';

$dir = basename(__DIR__);
$helper = Helper::getHelper($dir);
$helper->loadLanguage('manifesto');


// add an information claim to our payload
$claims = array_merge($assertClaims, array('data' => 'mydata'));

$token = TokenFactory::build('test', $claims, 120);

$script = <<<EOT
<script>
function myFunction()
{
    \$.ajax({
        url: 'ajax.php',
        dataType: 'json',
        beforeSend: function (xhr, settings) {
            xhr.setRequestHeader('Authorization', 'Bearer ' + '{$token}');
        },
        success: function (data) {
            // do something useful
            console.log(data.saw);
        },
        error: function() {
            // communicate issue to user
            alert('error');
        }
    });
}
</script>
EOT;

echo $script;
echo '<button onClick="myFunction()">Click me</button>';

require_once XOOPS_ROOT_PATH . '/footer.php';
```
