# Microservice application with continuous integration

**What is this repository?**
This is an open source project to create a continuous integration pipeline for building, testing and deploying a microservices application in a continuous integration environment.

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

# Quick Start

1.Create a directory for your project and enter into it

> $ mkdir project_name
> $ cd project_name

2.Create your microservice application with jhipster.

How to create a jhipster application:
http://jhipster.github.io/creating-an-app/

jhipster Microservices Architecure details:
http://jhipster.github.io/microservices-architecture/

_At this stage you should have two applications in your project, each one with its own folder "/project_name/gateway_app_name & /project_name/microservice_app_name"_

3.Download the .gitlab-ci.yml in your /project_name folder.

> $ wget https://raw.githubusercontent.com/ogomezm/microservices-ci/master/src/.gitlab-ci.yml

4.Create your Gitlab project and activate the ci and the docker repository.

Now you create a project in [gitlab.com](https://gitlab.com/) and go to project settings to activate the shared runners and container registry.

Configure your CI:
http://docs.gitlab.com/ce/ci/quick_start/README.html
_"For a quick start you can use shared runners, but please read the security considerations of using shared runners in the link above"_

Activate container registry:
http://about.gitlab.com/2016/05/23/gitlab-container-registry/

5.Edit the .gitlab-ci.yml to configure your build

>variables:
>  JHIPSTER_GATEWAY_APP: _"gateway_application_name"_
>  JHIPSTER_MICROSERVICE_APP: _"microservice_application_name"_
>  GITLAB_GROUP: _"group"_
>  GITLAB_PROJECT: _"project"_
  
_GITLAB_GROUP & GITLAB_PROJECT are your gitlab username and project name_

6.Push your code to the repository 

Go for one of your favorite drinks, it takes around 10 minutes to run your ci pipeline with an small jhipster project.

After 10 minutes...

Login into [gitlab.com](https://gitlab.com/)
Select your project
Go to Pipelines menu and see your build details.
Go to Container Registry menu and see your containers.

Enjoy!

# Beyond quick start

**Infrestructure as code**

> Create a folder within the project with the docker-compose name or something similar and enter into it.
> Then execute 
> $ yo jhipster:docker-compose

This will create all the needed files to bring the application up and running.
_"Find more details about docker-compose with jhipster in http://jhipster.github.io/docker-compose/ "_

Now update the images sources of the docker-compose.yml file to point to your gitlab docker repository.

> services:
>   application_name:
>       image: registry.gitlab.com/GITLAB_USER/PROJECT_NAME:APPLICATION_NAME

_"Note you have to do it for both gateway and microservices application"_

**Create Specific runners** 
(This allows you to create your own runners)
http://docs.gitlab.com/ce/ci/runners/README.html