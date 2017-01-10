title: Setting Up IntelliJ IDEA, Maven and Google Web Toolkit (GWT) for Java Development on Windows 10
slug: intellij-maven-google-web-toolkit-java-development-windows
meta: This tutorial shows how to configure a Java development environment on Windows 10 for Google Web Toolkit, Maven and IntelliJ.
category: post
date: 2017-01-05
modified: 2017-01-05
headerimage: /source/static/img/170105-intellij-gwt-maven-windows/header.jpg
headeralt: Java, Maven, Google Web Toolkit and IntelliJ logos. Copyright their respective owners.


Establishing a fresh Java development environment can be confusing but this
guide will quickly walk you through the steps to get set up on Windows 10.


## Our Tools
Our configuration walkthrough will involve several tools. Don't install
these bits just yet: we will walk through the steps together in a moment.

* Java 8 JDK
* JetBrains' IntelliJ IDEA the Java Integrated Development Environment (IDE)
* Apache Maven build and configuration tool
* Google Web Toolkit (GWT) web framework

Time to dive in and install our first tool.


## Installing Java 8
Start Windows and go to the Java 8 JDK downloads page in your web browser.
Read and accept the licensing agreement. Download the latest release of 
the Windows x64 Java SE Development Kit.

<img src="/source/static/img/170105-intellij-gwt-maven-windows/download-java-8-jdk.jpg" width="100%" class="technical-diagram img-rounded" alt="Java 8 JDK download page.">

When the download completes, run the executable. Allow the installer to make 
changes to your system.

<img src="/source/static/img/170105-intellij-gwt-maven-windows/allow-changes.jpg" width="100%" class="technical-diagram img-rounded" alt="Java 8 JDK make changes approval screen.">

Move through the installer and when you reach the following screen
press the "Change..." button.

<img src="/source/static/img/170105-intellij-gwt-maven-windows/jdk-change-directory.jpg" width="100%" class="technical-diagram img-rounded" alt="Change JDK installation directory.">

Modify the installation directory to `C:\devel\Java\jdk180_112` (or modify
the numbers based on the security release version you downloaded). Generally
it is easier to work with Java on the command line if there are no spaces 
in the directory names.

<img src="/source/static/img/170105-intellij-gwt-maven-windows/devel-jdk-install.jpg" width="100%" class="technical-diagram img-rounded" alt="Change JDK installation directory.">

Also change the JRE installation directory to somewhere without spaces.

<img src="/source/static/img/170105-intellij-gwt-maven-windows/change-jre-directory.jpg" width="100%" class="technical-diagram img-rounded" alt="Change JRE installation directory.">

Finish the installation process. Java will be added to your `PATH` 
environment variable but we also need to set `JAVA_HOME`. Open system
system settings for environment variables by searching for the term
"environment variables" next to the Start menu.

Settings by right clicking on the Start menu. Add a new environment
variable named `JAVA_HOME` with the value of the base directory to
your Java 8 JDK installation (not the `bin` subdirectory).

<img src="/source/static/img/170105-intellij-gwt-maven-windows/environment-variables.jpg" width="100%" class="technical-diagram img-rounded" alt="Set JAVA_HOME under environment variables.">

In this case, I installed the JDK to `C:\devel\Java\jdk180_112` so I set 
that as the value of `JAVA_HOME`.

Test that our installation proceeded correctly by opening up the 
command prompt. Search for "cmd" in the task bar search menu.

<img src="/source/static/img/170105-intellij-gwt-maven-windows/cmd-search.jpg" width="100%" class="technical-diagram img-rounded" alt="Command prompt search.">

Type `java -version` and press enter. You should see the exact Java version 
you just installed. That means you are good to go with the JDK.

<img src="/source/static/img/170105-intellij-gwt-maven-windows/java-version.jpg" width="100%" class="technical-diagram img-rounded" alt="Java version on the command line.">

Now that we have Java properly installed, we can set up Maven for our 
project builds and dependency management.


## Installing Maven
Head to the Apache Maven download page and grab the "binary zip 
archive" of the project. 

<img src="/source/static/img/170105-intellij-gwt-maven-windows/maven-download.jpg" width="100%" class="technical-diagram img-rounded" alt="Apache Maven download page.">

After the file finishes downloading, open it using File Explorer. Copy 
the directory within the zip file into your `C:\devel` folder.  

Add `C:\devel\maven\bin` (or whichever version you downloaded) as a value
in your `PATH` environment variable.

<img src="/source/static/img/170105-intellij-gwt-maven-windows/add-maven-to-path.jpg" width="100%" class="technical-diagram img-rounded" alt="Add Maven to PATH environment variable.">

Re-open the command prompt because environment variable changes such as this
one to the PATH variable only take effect within new command prompt windows, 
not ones that are already open.

Run `mvn -version` while *not* currently in the Maven installation directory. 
You should see output similar to the following text.

```
C:\devel>mvn -version
Apache Maven 3.3.9 (bb52d8502b132ec0a5a3f4c09453c07478323dc5; 2015-11-10T08:41:47-08:00)
Maven home: C:\devel\apache-maven-3.3.9\bin\..
Java version: 1.8.0_112, vendor: Oracle Corporation
Java home: C:\devel\Java\jdk180_112\jre
Default locale: en_US, platform encoding: Cp1252
OS name: "windows 10", version: "10.0", arch: "amd64", family: "dos"
```

If you instead receive an error stating that the `mvn` command cannot be found,
double check that Maven's `bin` directory was correctly set in the PATH variable.

We can next move on to installing Google Web Toolkit now that the Java JDK and
Maven are configured.


## Downloading and Configuring GWT
[Download GWT](http://www.gwtproject.org/download.html) and extract the
folder into `C:\devel` just as we did with Java and Maven.

The only step we need to do is also add the base GWT directory to our
PATH environment variable. Open the System Properties and Environment
Variables panel back up and add the GWT installation directory, such
as `C:\devel\gwt-2.8.0` as a value.

Test out the configuration by closing any existing command prompt
windows then opening a new one. Make sure your current directory is outside 
the GWT directory and type `webAppCreator`, one of GWT's important 
commands that creates new projects. If GWT was added to the `PATH` correctly
then the output should look like the following text.

```
C:\devel>webAppCreator
Missing required argument 'moduleName'                                                                                  Google Web Toolkit 2.8.0
WebAppCreator [-[no]overwriteFiles] [-[no]ignoreExistingFiles] [-templates template1,template2,...] [-out dir] [-junit pathToJUnitJar] [-[no]maven] [-[no]ant] moduleName

where
  -[no]overwriteFiles       Overwrite any existing files. (defaults to OFF)
  -[no]ignoreExistingFiles  Ignore any existing files; do not overwrite. (defaults to OFF)
  -templates                Specifies the template(s) to use (comma separeted). Defaults to 'sample,ant,eclipse,readme'
  -out                      The directory to write output files into (defaults to current)
  -junit                    Specifies the path to your junit.jar (optional)
  -[no]maven                DEPRECATED: Create a maven2 project structure and pom file (default disabled). Equivalent to specifying 'maven' in the list of templates. (defaults to OFF)
  -[no]ant                  DEPRECATED: Create an ant configuration file. Equivalent to specifying 'ant' in the list of templates. (defaults to OFF)
and
  moduleName                The name of the module to create (e.g. com.example.myapp.MyApp)
```

We can now create our first GWT web application project. Create a new directory
for our project named `firstProject` (or the name you want for your own project)
with the `mkdir` command, then move into that directory with `cd`:

```
mkdir firstProject
cd firstProject
```

Type the following command within the `C:\devel` directory to create the
boilerplate code for the GWT project.

```
webAppCreator com.fullstackjava.firstProject -templates "sample,maven,readme"
```

The `webAppCreator` will run and produce output like the following:

```
C:\devel\firstProject>webAppCreator com.fullstackjava.firstProject -templates "sample,maven,readme"
Generating from templates: [maven, readme, _sample-test, sample]
Created directory C:\devel\firstProject\src\test\java
Created directory C:\devel\firstProject\src\test\java\com\fullstackjava
Created directory C:\devel\firstProject\src\test\java\com\fullstackjava\client
Created directory C:\devel\firstProject\src\main\java
Created directory C:\devel\firstProject\src\main\java\com\fullstackjava
Created directory C:\devel\firstProject\src\main\java\com\fullstackjava\client
Created directory C:\devel\firstProject\src\main\java\com\fullstackjava\server
Created directory C:\devel\firstProject\src\main\java\com\fullstackjava\shared
Created directory C:\devel\firstProject\src\main\webapp
Created directory C:\devel\firstProject\src\main\webapp\WEB-INF
Created file C:\devel\firstProject\pom.xml
Created file C:\devel\firstProject\README.txt
Created file C:\devel\firstProject\src\test\java\com\fullstackjava\firstProjectJUnit.gwt.xml
Created file C:\devel\firstProject\src\test\java\com\fullstackjava\firstProjectSuite.java
Created file C:\devel\firstProject\src\test\java\com\fullstackjava\client\firstProjectTest.java
Created file C:\devel\firstProject\src\main\java\com\fullstackjava\firstProject.gwt.xml
Created file C:\devel\firstProject\src\main\java\com\fullstackjava\client\GreetingService.java
Created file C:\devel\firstProject\src\main\java\com\fullstackjava\client\GreetingServiceAsync.java
Created file C:\devel\firstProject\src\main\java\com\fullstackjava\client\firstProject.java
Created file C:\devel\firstProject\src\main\java\com\fullstackjava\server\GreetingServiceImpl.java
Created file C:\devel\firstProject\src\main\java\com\fullstackjava\shared\FieldVerifier.java
Created file C:\devel\firstProject\src\main\webapp\WEB-INF\web.xml
Created file C:\devel\firstProject\src\main\webapp\firstProject.css
Created file C:\devel\firstProject\src\main\webapp\firstProject.html
Created file C:\devel\firstProject\src\main\webapp\favicon.ico
```

GWT's `webAppCreator` command just built a new project with the necessary 
project structure to use Maven as our build tool.

Next we can set up IntelliJ as our Java integrated development environment.


## Setting up the IntelliJ Java IDE
In your web browser go to the JetBrains' IDEA Java IDE downloads page.

<img src="/source/static/img/170105-intellij-gwt-maven-windows/intellij-download.jpg" width="100%" class="technical-diagram img-rounded" alt="IntelliJ IDEA download page.">

Download the Ultimate Edition then open the downloaded `.exe` file.

<img src="/source/static/img/170105-intellij-gwt-maven-windows/associate-file-names-intellij.png" width="100%" class="technical-diagram img-rounded" alt="Associate file names IntelliJ.">

Check the boxes to associate `.java`, `.groovy` and `.kt` files with IntelliJ.
Complete the installation and check the box to run IntelliJ when done.

<img src="/source/static/img/170105-intellij-gwt-maven-windows/import-settings.png" width="100%" class="technical-diagram img-rounded" alt="Import settings from old IntelliJ.">


Read and accept the JetBrains Privacy Policy. Select "Evaluate for free" to 
use the free 30 day trial until you are ready to activate the full license.

You can now customize your settings or skip them for now and accept the 
defaults. Press the "Skip All and Set Defaults" button as the IDE will already 
have the settings we need for GWT development.

Move back over to the command prompt. We will test that Maven works with
the GWT project. Enter the following command from within the `firstProject` 
base directory where the `pom.xml` file was generated:

```
mvn compile
```

There will be a slew of output while Maven downloads the appropriate
project build dependencies. Maven should conclude with a `BUILD SUCCESS`
message like this one:

```
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 5 source files to C:\devel\firstProject\target\firstProject-1.0-SNAPSHOT\WEB-INF\classes
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 24.297 s
[INFO] Finished at: 2017-01-09T17:24:27-08:00
[INFO] Final Memory: 24M/171M
[INFO] ------------------------------------------------------------------------
```

Now the project is ready for some real work!


## Next Steps
You are all set to get cranking building your GWT app now that your local 
development environment is configured. Next you will want to take a 
look at the Twilio Voice, Twilio SMS and TaskRouter quickstarts to add 
communications into your new application.

Questions? Contact me via Twitter 
[@fullstackjava](https://twitter.com/fullstackjava)
or [@mattmakai](https://twitter.com/mattmakai). I'm also on GitHub as
[mattmakai](https://github.com/mattmakai).

Something wrong with this post? Fork 
[this page's source on GitHub](https://github.com/mattmakai/fullstackjava.com/blob/gh-pages/source/content/posts/170105-java-8-dev-env-windows-intellij-maven-gwt.markdown).
