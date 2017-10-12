## Building and running the sample using the command line

### Clone Git Repo
:pushpin: [Switch to Eclipse example](/docs/Using-WDT.md/#clone-git-repo)

```bash
$ git clone https://github.com/WASdev/sample.async.websockets.git
```

### Building the sample with Maven
:pushpin: [Switch to Eclipse example](/docs/Using-WDT.md/#building-the-sample-in-eclipse)

###### [Apache Maven](http://maven.apache.org/) commands

```bash
$ mvn install
```

You can skip tests with the following:

```bash
$ mvn install -DskipTests=true
```

In addition to publishing the WAR to the local Maven repository, the built WAR file is copied into the apps directory of the server configuration located in the async-websocket-wlpcfg directory:

```text
async-websocket-wlpcfg
 +- target
     +- async-websocket-wlpcfg-1.0.zip                         <-- packaged server file containing the server, application, and configuration
        +- wlp
            +- usr
                +- server
                    +- websocketSample
                        +- server.xml                          <-- server configuration
                        +- apps                                <- directory for applications
                            +- async-websocket-application.war <- sample application
                        +- logs                                <- created by running the server locally
                        +- workarea                            <- created by running the server locally
```

### Running the application locally with Maven
:pushpin: [Switch to Eclipse example](/docs/Using-WDT.md/#running-the-application-locally)

Change the current directory to the `async-websocket-wlpcfg` sub-project, and use the following commands to start the server and run the application:

To run the server in the foreground:

```bash
$ mvn liberty:run-server
```

To run the server in a background process:

```bash
$ mvn liberty:start-server
```

To stop the server:
```bash
$ mvn liberty:stop-server
```

### Building the sample with Gradle

This project can also be built and run with [Gradle]. The provided `build.gradle` file applies the [Liberty Gradle Plug-in] and is configured to automatically download and install the Liberty Java EE 7 Full Platform runtime from [Maven Central](http://search.maven.org/#search%7Cga%7C1%7Ccom.ibm.websphere.appserver.runtime). The Liberty Gradle Plug-in has built-in tasks that can be used to create, configure, and run the application on the Liberty server.

Use the following steps to run the application with the Gradle wrapper (Windows machines use `gradlew.bat`):

1. Execute the full Gradle build. The Liberty Gradle Plug-in will download and install the Liberty server.
    ```bash
    $ ./gradlew clean build
    ```
```text
async-websocket-wlpcfg
+- build
    +- wlp
        +- usr
            +- servers
                +- websocketSample
                    +- server.xml                          <-- server configuration
                    +- apps                                <-- directory for applications
                        +- async-websocket-application     <-- the websocket application
                    +- logs                                <-- created by running the server locally
                    +- workarea                            <-- created by running the server locally
```
### Running the application locally with Gradle

2. To start the server with the Websocket sample execute:
    ```bash
    $ ./gradlew libertyStart
    ```

    Alternatively, execute the run command:
    ```bash
    $ ./gradlew libertyRun --no-daemon
    ```
      
Once the server has started, the application will be available under [http://localhost:9082/websocket/](http://localhost:9082/websocket/).
    
3. To stop the server, execute:
    ```bash
    $ ./gradlew libertyStop
    ```  
Note, if Gradle is properly installed, Gradle commands can be executed directly using `gradle` and wouldn't require `gradlew`.

Please refer to the [Liberty Gradle Plug-in] repository for documentation about using the Liberty Gradle Plug-in.


[Liberty Gradle Plug-in]: https://github.com/WASdev/ci.gradle
[Gradle]: https://gradle.org
