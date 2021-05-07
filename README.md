graalvm-ce-deb
=====

[Graalvm Community Edition](https://github.com/oracle/graal) Debian package generator.

# How to Run

```sh
# Build with default settings (Java 11 JVM, amd64 architecture, Version 21.1.0)
./build

# Build with specific settings (Java 8 JVM, aarch64 architecture, Version 21.0.0)
JVM_VERSION=8 ARCHITECTURE=aarch64 GRAALVM_VERSION=21.0.0 ./build
```

# Installation

```sh
sudo dpkg -i {graalvm-deb-path}
```

# Making the GraalVM installation to primary JRE/JDK

For the installation includes `.jinfo` file, you can set the primary jre/sdk installation among the installed alternatives. This command sets all jre/jdk related binaries (`java`, `javac`, `javah`, etc.) to point the ones in the specified jre/jdk installation at once.

```
# This command sets java, javac, javah, ... to point the ones in the graalvm (java8) installation
update-java-alternatives --set /usr/lib/jvm/graalvm-ce-java8
```

If [fzf](https://github.com/junegunn/fzf) is installed on your system, you can select the primary installation interactively with the following command:

```sh
update-java-alternatives --list | awk '{print $1}' | fzf | xargs sudo update-java-alternatives --set
```

Note: `update-java-alternatives` only updates jre/jvm related alternatives; non-jvm binaries like `js`, `npm` or `gu` are not updated.

# Installing without existing Java
This package depends on `ca-certificates-java` which depends on a Java runtime.
GraalVM Java can be installed without a prior Java installation by doing following:
```sh
# Unpack package but don't configure it
dpkg --unpack graalvm-ce-<VERSION>.deb

# Install package dependencies. GraalVM package will be configured once its dependencies are installed
apt-get install ca-certificates-java java-common libnss3 libnspr4 libsqlite3-0
```

