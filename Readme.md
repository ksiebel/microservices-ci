**What is this repository?**
This is an open source project to build a continuous integration pipeline for building, testing and deploying a **jhipster** microservices application in a continuous integration environment.

**Notes**
This section describes some design principles and decisions.
 - Less is more
    _"This is actually easy as it has just started ;)"_
 - By now we assume you use jhipster to generate microservices application.
 - The jhipster application has to be packaged as docker containers and it uses docker-compose for deploying the application.
    _"jhipster it is already working with docker and docker-compose" 
 - It uses Gitlab as code repository, CI and docker registry.
    _"It provides both an on premises community version and a cloud service for free with unlimited repositories"_ 

**Notes for the future**
 - Other microservices application technology stacks will be added to this project in the future.
    _"The technology stacks has to use a yeoman scaffolding, so you can have a working microservices application with a CI pipeline in minutes, so the developer can focus in providing new functionalities."_    
 
**Quick Start**
TBD