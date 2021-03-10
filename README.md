# Stencil

Stencil is dynamic schema registry for protobuf. Protobuf is a great efficient and fast mechanism for serializing structured data. The challenge with protobuf is that for every change it requires to recompile the package to generate the necessary classes. This is not a big challenge if you have protobuf enclosed in your application and compile at startup. But if you have thousands of protos stored in central registry and 100s of applications use them. Updating dependencies of compiled proto jar can soon become a nightmare.

Protobuf allows you to define a whole proto file using [google.protobuf.FileDescriptorProto](https://github.com/protocolbuffers/protobuf/blob/master/src/google/protobuf/descriptor.proto#L62). A [google.protobuf.FileDescriptorSet](https://github.com/protocolbuffers/protobuf/blob/master/src/google/protobuf/descriptor.proto#L57) contains list of FileDescriptorProto. Stencil heavily make use of this feature to update proto schemas in runtime.


## Stencil server

### Installation

#### Compiling from source

Stencil server requires the following dependencies:

* Golang (version 1.16)
* Git


Run the following commands

```
$ git clone git@github.com:odpf/stencil.git
$ cd stencil
$ go build main.go
```

To run tests locally

```
$ make test
```


The config file used by application is `config.yaml` which should be present at the root of this directory. Example config you can check at `config.yaml.sample`

Execute following command to run the server
```
$ go run main.go serve
```
**Google Cloud storage as backend**\
  Set this env `GOOGLE_APPLICATION_CREDENTIALS` points to service account key file. `bucketURL` should start with `gs://`.

**Filesystem as backend**\
  `bucketURL` config should start with `file://`
