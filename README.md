# Attach Extended #

Gluon [Attach](http://gluonhq.com/products/mobile/attach/) is the component that addresses the integration with low-level platform APIs in an end-to-end Java Mobile solution.

Attach provides an uniform, platform-independent API to access device and hardware features. 
At runtime, the appropriate implementation (attach:desktop, attach:android, attach:ios) makes sure the platform specific code is 
used to deliver the functionality.

Attach is open source, and it is freely licensed under the GPL license.
[Gluon](http://gluonhq.com) can provide [custom consultancy](http://gluonhq.com/services/consulting/) and [training](http://gluonhq.com/services/training/), commercial licenses, and open source [commercial support](http://gluonhq.com/services/commercial-support/), including daily and monthly releases.

_What happens if Attach doesn't include the service or feature that you require?_

You can always ask for support (see previous links) to develop this service for you, but you could try to implement it on your own. 

Attach Extended is a demo project intended to show how to extend and create custom Attach services outside Attach itself. 

As a custom service, it can't use the `com.gluonhq.attach` package name. This avoids the need of modifying the GluonFX plugins to include the service, and it can be used as a regular dependency, with its platform classifiers.

Once the service has been tested in all possible platforms, it could be contributed to Attach via [Pull Request](https://github.com/gluonhq/attach/pulls).

## Building Attach Extended ##

### Requisites ###

These are the requisites:

* A recent version of [JDK 11](http://jdk.java.net/11/) or superior
* Gradle 6.0 or superior. 
* Attach Util 4.0.12 or superior

To build the iOS Services:
 
* A Mac with with MacOS X 10.14.4 or superior
* XCode 11.x or superior

To build the Android services:

* Android SDK and Android NDK (The GluonFX plugin installs both when building for Android)

### Attach Documentation ###

Read about Attach: [Device Interface](https://docs.gluonhq.com/#_device_interface)

The section [Building Attach](https://docs.gluonhq.com/#_building_attach) contains more advanced information.

### How to build and install Attach Extended ###

To build the Attach Extended services on the project's root, run:

`./gradlew clean build`

If you want to install them, run:

`./gradlew clean publishToMavenLocal`

When the process finishes successfully, the different services can be added to a Gluon Mobile project.

For instance, the Log service for desktop can be added to the project like:

```
<repositories>
    <repository>
        <id>Gluon</id>
        <url>https://nexus.gluonhq.com/nexus/content/repositories/releases</url>
    </repository>
</repositories>

<!-- dependencies -->
<dependency>
    <groupId>com.gluonhq.attachextended</groupId>
    <artifactId>log</artifactId>
    <version>4.0.12</version>
</dependency>
<dependency>
    <groupId>com.gluonhq.attachextended</groupId>
    <artifactId>log</artifactId>
    <version>4.0.12</version>
    <classifier>desktop</classifier>
    <scope>runtime</scope>
</dependency>
```

and used from the project like:

```
LogService.create().ifPresent(service -> service.log("This is a message"));
```
