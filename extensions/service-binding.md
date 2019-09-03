# Service Binding

## Buildpack Exposure

During the detection and build phases, the lifecycle MUST provide any bound services as files in `<platform>/services/<service-name>` with directory names matching the name of the bound service.

### Metadata
Within each service directory the lifecycle MUST provide a `metadata` directory containing a `kind`, `provider`, and `tags` files.  The value of the `kind` file MUST contain an abstract classification of the service.  The value of the `provider` file MUST identify the provider of this service.  The value of the `tags` file MUST contain a newline delimited collection of tags attached to the service.

In addition to the required files, the `metadata` directory MAY contain additional metadata about the service with file names and contents matching the metadata names and contents.

### Secret
Within each service directory the lifecycle MUST provide a `secret` directory containing the secrets associated with the service with filenames matching the secret name.

During the detection and build phases the contents of the files MAY be one of the following:

* empty
* the values of the secrets
* an indirect pointer to another system for value resolution

## Runtime Exposure

At runtime the lifecycle MUST provide any bound services as files in `<platform>/services/<service-name>` with directory names matching the name of the bound service.

## Metadata
Within each service directory the lifecycle MUST provide a `metadata` directory containing a `kind`, `provider`, and `tags` files.  The value of the `kind` file MUST contain an abstract classification of the service.  The value of the `provider` file MUST identify the provider of this service.  The value of the `tags` file MUST contain a newline delimited collection of tags attached to the service.

In addition to the required files, the `metadata` directory MAY contain additional metadata about the service with file names and contents matching the metadata names and contents.

### Secret
Within each service directory the lifecycle MUST provide a `secret` directory containing the secrets associated with the service with filenames matching the secret name.

During the detection and build phases the contents of the files MAY be one of the following:

* the values of the secrets
* an indirect pointer to another system for value resolution

The collection of files within the directory MAY change between application starts.  The collection of files within the directory MAY NOT change during the lifetime of the application.

The contents of the files MAY change between application starts.  The contents of the files MAY change during the lifetime of the application.

## Example Directory Structure
```plain
platform
└── services
    ├── primary-db
    │   ├── metadata
    │   │   ├── connection-count
    │   │   ├── kind
    │   │   ├── provider
    │   │   └── tags
    │   └── secret
    │       ├── endpoint
    │       ├── password
    │       └── username
    └── secondary-db
        ├── metadata
        │   ├── connection-count
        │   ├── kind
        │   ├── provider
        │   └── tags
        └── secret
            ├── endpoint
            ├── password
            └── username
```
