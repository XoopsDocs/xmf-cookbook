# ProxyCheck

`Xmf\ProxyCheck` handles proxy detection for `Xmf\IPAddress`

*Note: There is normally no direct use of this class outside of Xmf\IPAddress.*

If your XOOPS system runs behind a proxy such as a load balancer, by default [Xmf\IPAddress](ipaddress.md) will 
return the address of your proxy, not the client address.

To have IPAddress use ProxyCheck to report the client IP, establish a proxy_env key in 
*xoops_data/configs/xoopsconfig.php* that reflects the header name your proxy is configured to use to indicate 
the IP address of client that initiated the current request. Note that the value expected is the PHP $_SERVER variable 
key set to hold that header, not the actual HTTP header name.

Example for [RFC 7239](https://tools.ietf.org/html/rfc7239):

`'proxy_env' => 'HTTP_FORWARDED',`

Example for the common Client-IP header:

`'proxy_env' => 'HTTP_CLIENT_IP',`

Example for the common X-Forwarded-For header:

`'proxy_env' => 'HTTP_X_FORWARDED_FOR',`

If the $_SERVER key specified in `proxy_env` exists, the IP address specified in that header will be used by 
`Xmf\IPAddress` if it is valid and routable.

**Note:** This class is intended to be used only with a proxy you (or your hosting) control that sets the header you 
specifed. That proxy should also NOT forward to you any proxy related headers it did not set. Relying on the IP address 
in any other context, such as trying to peer behind a client side proxy, raises **serious security concerns**.