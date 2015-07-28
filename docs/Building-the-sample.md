This sample can be built using either [Gradle](#building-with-gradle) or [Maven](#building-with-maven).

In addition to publishing the war to the local maven repository, the built war file is copied into the apps directory of the server configuration located in the async-websocket-wlpcfg directory:

```text
async-websocket-wlpcfg
 +- servers
     +- websocketSample                        <-- specific server configuration
        +- server.xml                          <-- server configuration
        +- apps                                <- directory for applications
           +- async-websocket-application.war  <- sample application
        +- logs                                <- created by running the server locally
        +- workarea                            <- created by running the server locally
```

## Building with Gradle

This sample can be build using [Gradle](http://gradle.org/).

```bash
$ gradle build publishToMavenLocal
```

## Building with maven

This sample can be build using [Apache Maven](http://maven.apache.org/).

* [Build without a server](#build-without-server)
* [Build with a provided server](#build-with-a-provided-server)
* [Build by downloading a new server](#build-by-downloading-a-new-server)

#### Build without server

```bash
$ mvn install
```
Creates and install the artifact in your local maven repository with the server definition and the sample.

#### Build with a provided server

```bash
$ mvn install -Pprovided-wlp -Dwlp.install.dir=<installation_folder_of_wlp>
```
Creates a new server named websocketSample with all configurations and files for running the sample by providing an existing installation of liberty.

#### Build by downloading a new server

```bash
$ mvn install -Pdownload-wlp -Dwlp.version=<liberty_version> -Dwlp.edition=<liberty_edition> -Dwlp.install.dir=<installation_folder_of_wlp>
```
Downloads and creates a new server named websocketSample with all configurations and files for running the sample. 

If `wlp.install.dir` parameter is not provided, then it will be downloaded in `${project.build.outputDirectory}` (the target/classes directory of your project).

Available versions:

* 8.5.5.6

Available editions:

* wlp-javaee7
* wlp-webProfile7

## Next step

[Downloading WAS Liberty](/docs/Downloading-WAS-Liberty.md)