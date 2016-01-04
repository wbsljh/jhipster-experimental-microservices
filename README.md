This is an EXPERIMENTAL, TEMPORARY repository for JHipster using microservices
============

## Introduction

This repository is:

- EXPERIMENTAL
- TEMPORARY

This is a proof of concept of using JHipster in a microservices architecture, using:

- [The Netflix OSS stack](https://netflix.github.io/)
- [Spring Cloud Netflix](http://cloud.spring.io/spring-cloud-netflix/)

## What is currently provided

- __JHiRegistry__ is an application registry, based on Netflix Eureka
- __JHiRouter__ is a JHipster application which is also a router, based on Netflix Zuul
- __JHiDashboard__ is a monitoring dashboard, based on Netflix Turbine
- __app1__ is a JHipster application, which registers itself to JHiRegistry

## How to use it

Run `mvn` on each project to get them running.

- JHiRouter and app1 will register themselves to JHiRegistry
- JHiRouter will route requests to `/api/foos` to app1 (you will get security issues, see what's missing below)

You can also run several app1 instances by changing their Spring Boot `server.port` property, and you will see them in JHiRegistry.

## What is missing

- Security: this must be done using OAuth2 at least. If this is done with an OAuth2 server, it will be with the Spring Security implementation, and will be called JHiSecurity
- Monitoring and logging: this should be done using the ELK stack, with Logstash handling the Spring Boot logs

## What should be done

- Have a nice uniform UI for everything: JHiRegistry and JHiDashboard should be available in the Admin dashboard of JHiRouter, with the usual JHipster UI
- JHiRouter should also have an admin UI to add/remove/edit routes at runtime: Zuul allows this using a Cassandra backend, we might also need to implement another backend (which is easy).
- Have some validated workflows to work on AngularJS (served by JHiRouter) and a REST endpoint served by a backend application (and routed by JHiRouter)

## What will be done in the future

- JHiRegistry, JHiDashboard and JHiSecurity will be standalone applications.
- JHiRouter might be a standalone application, or be generated by JHipster (still needs to be discussed)
- JHipster applications will have a new option to register themselves to Eureka
