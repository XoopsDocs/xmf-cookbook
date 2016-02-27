# Yaml
`Xmf\Yaml` supports serializing data to YAML, and deserializing YAML to PHP data.

[YAML](http://yaml.org/) is a markup language designed for human friendliness. It is useful for
configuration files, database schemas, data import/export and more.

## Basic YAML Serializing and Deserializing

### Yaml::dump(*$var*)

Dump an PHP array *$var* as a YAML string

### Yaml::load(*$yamlString*)

Load a YAML string *$yamlString* into a PHP array

## Saving to and Reading from Files

### Yaml::read(*$yamlFile*)

Read the file *$yamlFile* containing YAML into a PHP array

### Yaml::save(*$var*, *$yamlFile*)

Save a PHP array *$var* as a YAML file *$yamlFile*.

## Wrapped YAML

When YAML data is saved to a text file, if that file is exposed via a web server, the data can be easily
read using a browser. Best practice would be to place sensitive files outside of the web root in a secured
directory, with names that cannot be easily predicted. This is not always possible.

In circumstances where a YAML file might be served directly through a web server, `Xmf\Yaml` provides
*wrapped* versions of all the basic functions, dump(), load(), read() and save(). These work by storing
a YAML document wrapped as comments within a small PHP wrapper. This wrapped data should be saved in a file
with a *.php* extension.

If directly accessed by the web server, such a wrapped file will be executed as PHP, producing blank output.

Inside the wrapped file, the YAML document is marked in the file with a line consisting of three dashes ("---")
and ending with a line consisting three dots ("...") as documented in the
[YAML specifications](http://yaml.org/spec/1.1/#id857577).

The base functions do not support the document within a stream format. The wrapped forms support a single
marked document with a YAML stream. If a stream does not contain a marked document, the entire stream will be
treated as a YAML stream.

### Yaml::dumpWrapped(*$var*)
Dump an PHP array *$var*as a YAML string with a php wrapper

### Yaml::loadWrapped(*$yamlString*)
Load a YAML string *$yamlString* with a php wrapper into a PHP array

### Yaml::readWrapped(*$yamlFile*)
Read a file *$yamlFile* containing YAML with a php wrapper into a PHP array

### Yaml::saveWrapped(*$var*, *$yamlFile*)
Save a PHP array *$var* as a YAML file *$yamlFile* with a php wrapper
