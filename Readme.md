# Microservice application with continuous integration

**What is this repository?**
This is an open source project to build a continuous integration pipeline for building, testing and deploying a microservices application in a continuous integration environment.

**Objective**
 - The goal is to have a microservices application with a CI pipeline in a few minutes.
 
**Notes**
This section describes some design principles and decisions.
 - **Docker** it is used to package the application artifacts and its dependencies.
 - This project assumes you are defining your **infrastructure as code** using docker-compose. 
 - By now we assume you use **jhipster** to generate microservices application.
    _"The jhipster microservice application has to be packaged as docker containers and use docker-compose for CI environment deployment."_
 - It uses **Gitlab** as code repository, CI and docker registry.

**Notes for the future**
 - Mode code repositories will be added in future releases.
 - It has to be microservice application technology stack agnostic. 
    _"As far the technology stack supports using docker to package the application and it is generated using yeoman scaffolding"_

**Quick Start**

1.Create a directory for your project and enter into it

$ mkdir project_name
$ cd project_name

2.Create your microservice application with jhipster.

http://jhipster.github.io/creating-an-app/

http://jhipster.github.io/microservices-architecture/

_At this stage you should have two applications in your project each one with its own folder._
_"/project_name/gateway_app_name & /project_name/microservice_app_name"_

3.Download the .gitlab-ci.yml in your /project_name folder.

$ wget https://raw.githubusercontent.com/ogomezm/microservices-ci/master/src/.gitlab-ci.yml

4.Edit the .gitlab-ci.yml to configure your build

>variables:
>  JHIPSTER_GATEWAY_APP: _"gateway_application_name"_
>  JHIPSTER_MICROSERVICE_APP: _"microservice_application_name"_
>  GITLAB_GROUP: _"group"_
>  GITLAB_PROJECT: _"project"_
  
_GITLAB_GROUP & GITLAB_PROJECT are your gitlab username and project_name_
