# README

`Xmf\Yaml` supports serializing data to YAML, and deserializing YAML to PHP data.

[YAML](http://yaml.org/) is a markup language designed for human friendliness. It is useful for configuration files, database schemas, data import/export and more.

## Basic YAML Serializing and Deserializing

### Yaml::dump\(_$var_\)

Dump an PHP array _$var_ as a YAML string

### Yaml::load\(_$yamlString_\)

Load a YAML string _$yamlString_ into a PHP array

## Saving to and Reading from Files

### Yaml::read\(_$yamlFile_\)

Read the file _$yamlFile_ containing YAML into a PHP array

### Yaml::save\(_$var_, _$yamlFile_\)

Save a PHP array _$var_ as a YAML file _$yamlFile_.

## Wrapped YAML

When YAML data is saved to a text file, if that file is exposed via a web server, the data can be easily read using a browser. Best practice would be to place sensitive files outside of the web root in a secured directory, with names that cannot be easily predicted. This is not always possible.

In circumstances where a YAML file might be served directly through a web server, `Xmf\Yaml` provides _wrapped_ versions of all the basic functions, dump\(\), load\(\), read\(\) and save\(\). These work by storing a YAML document wrapped as comments within a small PHP wrapper. This wrapped data should be saved in a file with a _.php_ extension.

If directly accessed by the web server, such a wrapped file will be executed as PHP, producing blank output.

Inside the wrapped file, the YAML document is marked in the file with a line consisting of three dashes \("---"\) and ending with a line consisting three dots \("..."\) as documented in the [YAML specifications](http://yaml.org/spec/1.1/#id857577).

The base functions do not support the document within a stream format. The wrapped forms support a single marked document with a YAML stream. If a stream does not contain a marked document, the entire stream will be treated as a YAML stream.

### Yaml::dumpWrapped\(_$var_\)

Dump an PHP array _$var_ as a YAML string with a php wrapper

### Yaml::loadWrapped\(_$yamlString_\)

Load a YAML string _$yamlString_ with a php wrapper into a PHP array

### Yaml::readWrapped\(_$yamlFile_\)

Read a file _$yamlFile_ containing YAML with a php wrapper into a PHP array

### Yaml::saveWrapped\(_$var_, _$yamlFile_\)

Save a PHP array _$var_ as a YAML file _$yamlFile_ with a php wrapper

