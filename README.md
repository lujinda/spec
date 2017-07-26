# Container Storage Interface (CSI) Specification [![build status](https://travis-ci.org/container-storage-interface/spec.svg?branch=master)](https://travis-ci.org/container-storage-interface/spec)

![CSI Logo](logo.png)

This project contains the CSI [specification](spec.md). Please see the
[build reference](#build-reference) section for information on how to
generate the protobuf or Go source files.

## Build Reference
This section describes how to generate the CSI protobuf file, generate
Go sources from the protobuf, and which environment variables can
influence the build process.

### Generate Protobuf
The CSI protobuf can be generated with the following command:

```bash
$ make csi.proto
```

In the above example the protobuf file is generated by parsing a `spec.md`
from a remote git repository (this one in fact). However, it's also
possible to generate the protobuf from a local spec file:

```bash
$ CSI_SPEC_FILE=spec.md make csi.proto
```

### Generate Go Source
The following command generates the Go source file from the protobuf:

```bash
$ make csi.pb.go
```

### Build Options
It's also possible to influence the location from which the CSI specification
is retrieved with the following environment variables:

| Name | Description | Default |
|------|-------------|---------|
| `CSI_SPEC_FILE` | The path to a local spec file used to generate the protobuf | |
| `CSI_GIT_OWNER` | The GitHub user or organization that owns the git repository that contains the CSI spec file | `container-storage-interface` |
| `CSI_GIT_REPO` | The GitHub repository that contains the CSI spec file | `spec` |
| `CSI_GIT_REF` | The git ref to use when getting the CSI spec file. This value can be a branch name, a tag, or a git commit ID | `master` |
| `CSI_SPEC_NAME` | The name of the CSI spec markdown file | `spec.md` |
| `CSI_SPEC_PATH` | The remote path of the CSI markdown file | |
| `CSI_PROTO_NAME` | The name of the protobuf file to generate. This value should not include the file extension | `csi` |
| `CSI_PROTO_DIR` | The path of the directory in which the protobuf and Go source files will be generated. If this directory does not exist it will be created. | `.` |
| `CSI_PROTO_ADD` | A list of additional protobuf files used when building the Go source file | |
| `CSI_IMPORT_PATH` | The package of the generated Go source | `csi` |
