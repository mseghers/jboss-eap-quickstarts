Red Hat JBoss Enterprise Application Platform (EAP) Quickstarts
====================
Summary: The quickstarts demonstrate Java EE 6 and a few additional technologies from the JBoss stack. They provide small, specific, working examples that can be used as a reference for your own project.

Introduction
------------

These quickstarts run on Red Hat JBoss Enterprise Application Platform 6.1 or later. We recommend using the JBoss EAP ZIP file. This version uses the correct dependencies and ensures you test and compile against your runtime environment. 

Be sure to read this entire document before you attempt to work with the quickstarts. It contains the following information:

* [Available Quickstarts](#available-quickstarts): List of the available quickstarts and details about each one.

* [Suggested Approach to the Quickstarts](#suggested-approach-to-the-quickstarts): A suggested approach on how to work with the quickstarts.

* [System Requirements](#system-requirements): List of software required to run the quickstarts.

* [Configure Maven]((https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/CONFIGURE_MAVEN.md#configure-maven-to-build-and-deploy-the-quickstarts)): How to configure the Maven repository for use by the quickstarts.

* [Run the Quickstarts](#run-the-quickstarts): General instructions for building, deploying, and running the quickstarts.

* [Run the Arquillian Tests](#run-the-arquillian-tests): How to run the Arquillian tests provided by some of the quickstarts.

* [Optional Components](#optional-components): How to install and configure optional components required by some of the quickstarts.


Available Quickstarts
---------------------

The list of all currently available quickstarts can be found here: <http://site-jdf.rhcloud.com/quickstarts/get-started/>. The table lists each quickstart name, the technologies it demonstrates, gives a brief description of the quickstart, and the level of experience required to set it up. For more detailed information about a quickstart, click on the quickstart name.

Some quickstarts are designed to enhance or extend other quickstarts. These are noted in the **Prerequisites** column. If a quickstart lists prerequisites, those must be installed or deployed before working with the quickstart.

Quickstarts with tutorials in the [Get Started Developing Applications](http://www.jboss.org/jdf/quickstarts/jboss-as-quickstart/guide/Introduction/ "Get Started Developing Applications") are noted with two asterisks ( ** ) following the quickstart name. 

_Note: Some of these quickstart use the H2 database included with JBoss EAP 6. It is a lightweight, relational example datasource that is used for examples only. It is not robust or scalable and should NOT be used in a production environment!_

[TOC-quickstart]

Suggested Approach to the Quickstarts
-------------------------------------

We suggest you approach the quickstarts as follows:

* Regardless of your level of expertise, we suggest you start with the **helloworld** quickstart. It is the simplest example and is an easy way to prove your server is configured and started correctly.
* If you are a beginner or new to JBoss, start with the quickstarts labeled **Beginner**, then try those marked as **Intermediate**. When you are comfortable with those, move on to the **Advanced** quickstarts.
* Some quickstarts are based upon other quickstarts but have expanded capabilities and functionality. If a prerequisite quickstart is listed, be sure to deploy and test it before looking at the expanded version.


System Requirements
-------------------

The applications these projects produce are designed to be run on Red Hat JBoss Enterprise Application Platform 6.1 or later. 

To run these quickstarts with the provided build scripts, you need the following:

1. Java 1.6, to run JBoss AS and Maven. You can choose from the following:
    * OpenJDK
    * Oracle Java SE
    * Oracle JRockit

2. Maven 3.0.0 or newer, to build and deploy the examples
    * If you have not yet installed Maven, see the [Maven Getting Started Guide](http://maven.apache.org/guides/getting-started/index.html) for details.
    * If you have installed Maven, you can check the version by typing the following in a command prompt:

            mvn --version 

3. The JBoss EAP distribution ZIP.
    * For information on how to install and run JBoss, refer to the product documentation located on the Customer Portal here: <https://access.redhat.com/site/documentation/en-US/JBoss_Enterprise_Application_Platform/>.

4. You can also use [JBoss Developer Studio or Eclipse](#use-jboss-developer-studio-or-eclipse-to-run-the-quickstarts) to run the quickstarts. 


Run the Quickstarts
-------------------

The root folder of each individual quickstart contains a README file with specific details on how to build and run the example. In most cases you do the following:

* [Start the JBoss server](#start-the-jboss-server)
* [Build and deploy the quickstarts](#build-and-deploy-the-quickstarts)


### Start the JBoss Server

Before you deploy a quickstart using the Maven command line tool, in most cases you need a running JBoss EAP server. A few of the Arquillian tests do not require a running server. This will be noted in the README for that quickstart. 

The JBoss server can be started a few different ways.

* [Start the Default JBoss Server](#start-the-default-jboss-server): This is the default configuration. It defines minimal subsystems and services.
* [Start the JBoss Server with the _full_ profile](#start-the-jboss-server-with-the-full-profile): This profile configures many of the commonly used subsystems and services.
* [Start the JBoss Server with a custom configuration](#start-the-jboss-server-with-custom-configuration-options): Custom configuration parameters can be specified on the command line when starting the server.

The README for each quickstart will specify which configuration is required to run the example.

#### Start the Default JBoss Server

To start JBoss EAP:

1. Open a command prompt and navigate to the root of the JBoss server directory.
2. The following shows the command line to start the JBoss server:

        For Linux:   JBOSS_HOME/bin/standalone.sh
        For Windows: JBOSS_HOME\bin\standalone.bat

#### Start the JBoss Server with the Full Profile

To start JBoss EAP with the Full Profile:

1. Open a command prompt and navigate to the root of the JBoss server directory.
2. The following shows the command line to start the JBoss server with the full profile:

        For Linux:   JBOSS_HOME/bin/standalone.sh -c standalone-full.xml
        For Windows: JBOSS_HOME\bin\standalone.bat -c standalone-full.xml

#### Start the JBoss Server with Custom Configuration Options

To start JBoss EAP with custom configuration options:

1. Open a command prompt and navigate to the root of the JBoss server directory.
2. The following shows the command line to start the JBoss server. Replace the CUSTOM_OPTIONS with the custom optional parameters specified in the quickstart.

        For Linux:   JBOSS_HOME/bin/standalone.sh CUSTOM_OPTIONS
        For Windows: JBOSS_HOME\bin\standalone.bat CUSTOM_OPTIONS
           
### Build and Deploy the Quickstarts

See the README file in each individual quickstart folder for specific details and information on how to run and access the example. 

_Note:_ If you do not configure the Maven settings as described here, [Configure Maven](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/CONFIGURE_MAVEN.md#configure-maven-to-build-and-deploy-the-quickstarts), you must pass the configuration setting on every Maven command as follows: ` -s QUICKSTART_HOME/settings.xml`


#### Build the Quickstart Archive

In most cases, you can use the following steps to build the application to test for compile errors or to view the contents of the archive. See the specific quickstart README file for complete details.

1. Open a command prompt and navigate to the root directory of the quickstart you want to build.
2. Use this command if you only want to build the archive, but not deploy it:
   * If you have configured the Maven settings :

            mvn clean install
   * If you have NOT configured settings Maven settings:

            mvn clean install -s QUICKSTART_HOME/settings.xml

#### Build and Deploy the Quickstart Archive

In most cases, you can use the following steps to build and deploy the application. See the specific quickstart README file for complete details.

1. Make sure you [start the JBoss server](#start-the-jboss-server) as described in the README.
2. Open a command prompt and navigate to the root directory of the quickstart you want to run.
3. Use this command to build and deploy the archive:

   * If you have configured the Maven settings :

            mvn clean install jboss-as:deploy
   * If you have NOT configured the Maven settings :

            mvn clean install jboss-as:deploy -s QUICKSTART_HOME/settings.xml

#### Undeploy an Archive

The command to undeploy the quickstart is simply: 

        mvn jboss-as:undeploy


### Verify the Quickstarts Build with One Command
-------------------------------------------------

You can verify the quickstarts build using one command. However, quickstarts that have complex dependencies must be skipped. For example, the _jax-rs-client_ quickstart is a RESTEasy client that depends on the deployment of the _helloworld-rs_ quickstart. As noted above, the root `pom.xml` file defines a `complex-dependencies` profile to exclude these quickstarts from the root build process. 

To build the quickstarts:

1. Do not start the JBoss server.
2. Open a command prompt and navigate to the root directory of the quickstarts.
3. Use this command to build the quickstarts that do not have complex dependencies:

   * If you have configured the Maven settings :

            mvn clean install '-Pdefault,!complex-dependencies'

   * If you have NOT configured the Maven settings :

            mvn clean install '-Pdefault,!complex-dependencies' -s QUICKSTART_HOME/settings.xml

_Note_: If you see a `java.lang.OutOfMemoryError: PermGen space` error when you run this command, increase the memory by typing the following command for your operating system, then try the above command again.

        For Linux:   export MAVEN_OPTS="-Xmx512m -XX:MaxPermSize=128m"
        For Windows: SET MAVEN_OPTS="-Xmx512m -XX:MaxPermSize=128m"


### Undeploy the Deployed Quickstarts with One Command
------------------------------------------------------

To undeploy the quickstarts from the root of the quickstart folder, you must pass the argument `-fae` (fail at end) on the command line. This allows the command to continue past quickstarts that fail due to complex dependencies and quickstarts that only have Arquillian tests and do not deploy archives to the server.

You can undeploy quickstarts using the following procedure:

1. Start the JBoss server.
2. Open a command prompt and navigate to the root directory of the quickstarts.
3. Use this command to undeploy any deployed quickstarts:

            mvn jboss-as:undeploy -fae

To undeploy any quickstarts that fail due to complex dependencies, follow the undeploy procedure described in the quickstart's README file.


Run the Arquillian Tests
------------------------

Some of the quickstarts provide Arquillian tests. By default, these tests are configured to be skipped, as Arquillian tests an application on a real server, not just in a mocked environment.

You can either start the server yourself or let Arquillian manage its lifecycle during the testing. The individual quickstart README should tell you what to expect in the console output and the server log when you run the test.

_Note:_ If you do not configure the Maven settings as described here, [Configure Maven](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/CONFIGURE_MAVEN.md#configure-maven-to-build-and-deploy-the-quickstarts), you must pass the configuration setting on every Maven command as follows: ` -s QUICKSTART_HOME/settings.xml`

1. Test the quickstart on a remote server
    * Arquillian's remote container adapter expects a JBoss server instance to be already started prior to the test execution. You must [Start the JBoss server](#start-the-jboss-server) as described in the quickstart README file.
    * If you need to run the tests on a JBoss server running on a machine other than localhost, you can configure this, along with other options, in the `src/test/resources/arquillian.xml` file using the following properties:
        
            <container qualifier="jboss" default="true">
                <configuration>
                    <property name="managementAddress">myhost.example.com</property>
                    <property name="managementPort">9999</property>
                    <property name="username">customAdminUser</property>
                    <property name="password">myPassword</property>
                </configuration>
            </container>    
    * Run the test goal with the following profile activated:

            mvn clean test -Parq-jbossas-remote     
2. Test the quickstart on a managed server

    Arquillian's managed container adapter requires that your server is not running as it will start the container for you. However, you must first let it know where to find the JBoss server directory. The simplest way to do this is to set the `JBOSS_HOME` environment variable to the full path to your JBoss server directory. Alternatively, you can set the path in the `jbossHome` property in the Arquillian configuration file.
    * Open the `src/test/resources/arquillian.xml` file located in the quickstart directory.
    * Find the configuration for the JBoss container. It should look like this:

            <!-- Example configuration for a managed/remote JBoss EAP 6 instance -->
            <container qualifier="jboss" default="true">
                <!-- If you want to use the JBOSS_HOME environment variable, just delete the jbossHome property -->
                <!--<configuration> -->
                <!--<property name="jbossHome">/path/to/jboss/as</property> -->
                <!--</configuration> -->
            </container>           
    * Uncomment the `configuration` element, find the `jbossHome` property and replace the "/path/to/jboss/as" value with the actual path to your JBoss EAP server.
    * Run the test goal with the following profile activated:

            mvn clean test -Parq-jbossas-managed


Use JBoss Developer Studio or Eclipse to Run the Quickstarts
------------------------------------------------------------

You can also deploy the quickstarts from Eclipse using JBoss tools. For more information on how to set up Maven and the JBoss tools, refer to the [JBoss Enterprise Application Platform Development Guide](https://access.redhat.com/site/documentation/JBoss_Enterprise_Application_Platform/) or [Get Started Developing Applications](http://www.jboss.org/jdf/quickstarts/jboss-as-quickstart/guide/Introduction/ "Get Started Developing Applications").


Optional Components
-------------------
The following components are needed for only a small subset of the quickstarts. Do not install or configure them unless the quickstart requires it.

* [Create Users Required by the Quickstarts](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/CREATE_USERS.md#create-users-required-by-the-quickstarts): Add a Management or Application user for the quickstarts that run in a secured mode.

* [Configure the PostgreSQL Database for Use with the Quickstarts](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/CONFIGURE_POSTGRESQL.md#configure-the-postgresql-database-for-use-with-the-quickstarts): The PostgreSQL database is used for the distributed transaction quickstarts.

* [Configure Byteman for Use with the Quickstarts](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/CONFIGURE_BYTEMAN.md#configure-byteman-for-use-with-the-quickstarts): This tool is used to demonstrate crash recovery for distributed transaction quickstarts.



