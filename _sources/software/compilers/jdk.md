# OpenJDK

Java is a programming language and runtime environment used by many research applications and tools. Calder provides OpenJDK, an open-source implementation of the Java Platform.

OpenJDK is provided as the recommended option for Java on Calder. Oracle's Java distribution has different licensing terms, so users should use the provided OpenJDK versions unless they have a specific requirement that needs further consideration.

## Available versions

### Default Java version

OpenJDK 17 is available by default when you log in to Calder. No additional module needs to be loaded to use this version.

### OpenJDK 25

Calder also provides OpenJDK 25.0.2. To use it, load the Calder CPU environment and the OpenJDK module:

```bash
module load calder/cpu
module load openjdk/25.0.2_10
```

Check the active version with:

```bash
java --version
```

## Additional Java libraries and tools

The OpenJDK installation provides the Java runtime and development tools. If your application requires additional Java libraries, frameworks or other dependencies, you may need to obtain and configure them separately according to the application's documentation.
