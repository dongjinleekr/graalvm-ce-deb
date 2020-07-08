graalvm-ce-deb
=====

[Graalvm Community Edition](https://github.com/oracle/graal) Debian package generator.

# How to Run

```sh
# Build with default settings (Java 8 JVM, amd64 architecture, Version 20.1.0)
./build

# Build with specific settings (Java 11 JVM, aarch64 architecture, Version 20.0.0)
JVM_VERSION=11 ARCHITECTURE=aarch64 GRAALVM_VERSION=20.0.0 ./build
```

