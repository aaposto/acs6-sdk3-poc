# SDK 3 - ACS 6.0 project

This project uses SDK 3.0.1 in conjunction with ACS 6.0 and preserves RAD features for the newest Alfresco Content Services release.


## Prerequisites

These prerequisites are necessary for getting this project up and running.

* JDK 8 needs to be installed
* Maven 3.3 or a newer version
* Docker CE 18.03.0-ce or newer

## Preparation for first run

* Grab latest CE war from Alfresco public repositories and save it locally
At the  time of writing, I used `https://artifacts.alfresco.com/nexus/service/local/repo_groups/public/content/org/alfresco/content-services-community/6.0.5-ea/content-services-community-6.0.5-ea.war`

* Install Alfresco Repository to your local .m2 repository
```
$ mvn install:install-file -DgroupId=org.alfresco -DartifactId=alfresco-platform -Dversion=6.0.5-ea -Dpackaging=war -Dfile=/path/to/content-services-community-6.0.5-ea.war
```

## Running your project locally

You can do the following :

* Start the docker containers needed for your DEV environment
```
$ docker-compose up -d
```
* Run the embedded maven tomcat using the alfresco-plugin
```
$ mvn clean install alfresco:run
```
* Stop all docker containers
```
$ docker-compose stop
```

Or you can use the `run.sh`/`run.bat` scripts to do that for you.

## Known issues

* Since the SDK was compiled to run in conjunction with previous Alfresco versions, the upgraded dependencies in the repo cause some errors in the logs during TOMCAT shutdown after integration-tests

## Extra notes

If you are reading this, you would probably be interested in checking out these links :
* https://github.com/Alfresco/alfresco-repository/wiki/ACS-6-Migration-Guide#jackson
* https://community.alfresco.com/community/ecm/blog/2018/04/24/migrating-alfresco-sdk2-projects-to-acs-6
