# SimpleSAMLPHP Docker Image

A docker image for SimpleSAMLPHP. Right now the image is only useful for
configuring a Service Provider.

## Usage

### Configuration

The image uses [bander2/twit](https://github.com/bander2/twit) CLI template tool
to configure SimpleSAMLPHP at runtime. In order to configure the container,
create a YAML file with your configuration. For example:

```yml
# myparams.yml
entity_id:     This is a secret
secretsalt:    This is a secret
adminpassword: This is a secret
authsources:
  - name: This is a secret
    idp:  This is a secret
metadata:
  - entityid:       This is a secret
    metadata_set:   This is a secret
    ssos:
      binding:      This is a secret
      location:     This is a secret
    slo:
      binding:      This is a secret
      location:     This is a secret
    certdata:       This is a secret
    name_id_format: This is a secret

```

For a complete list of configuration, reference the
[params.yml.dist](params.yml.dist) file. For configuration not specified, the
values in params.yml.dist are used as defaults.

### Running

Mount your configuration to /params.yml in the container and the entrypoint
script will write the SimpleSAMLPHP configuration:

```
$ docker run -v $(pwd)/myparams.yml:/params.yml banderson/simplesamlphp
```
