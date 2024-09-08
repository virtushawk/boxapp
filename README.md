# boxapp
This pet project is designed to help learn and demonstrate the implementation of a microservices architecture using various modern tools and dependencies

### Overview

The Boxapp Microservice project is a sample application built with Spring Boot that manages user-event relations. It integrates with several microservices tools to provide robust, distributed, and scalable solutions.

### Key Features

- **Spring Boot**: Leverage the power and simplicity of Spring Boot for building and managing microservices.
- **Spring Cloud**: Utilize Spring Cloud components for service discovery, configuration management, and resilience.
- **PostgreSQL**: Use PostgreSQL for reliable and efficient relational database management.
- **RabbitMQ**: Enable efficient messaging and communication between services.
- **Redis**: Implement caching to improve performance and scalability.
- **Spring Data JPA**: Simplify database operations with Spring Data JPA.
- **Resilience4j**: Enhance fault tolerance and resilience using Resilience4j.
- **OpenFeign**: Facilitate easy and declarative REST clients with OpenFeign.
- **Eureka**: Enable service discovery with Netflix Eureka.
- **Micrometer**: Gain insights and metrics with Micrometer and tracing with Brave.
- **Papertrail**: Centralize and monitor your logs with Papertrail.
- **Zipkin**: Implement distributed tracing with Zipkin to monitor and troubleshoot latency issues in your microservices.

Below are the major technologies and dependencies used in this project:

#### Spring Boot
- **spring-boot-starter-actuator**: For monitoring and managing your application.
- **spring-boot-starter-web**: For creating RESTful web applications.
- **spring-boot-devtools**: For a faster development experience.
- **spring-boot-starter-test**: For comprehensive testing support.
- **spring-boot-starter-data-jpa**: For easy data access and manipulation using JPA.
- **spring-boot-starter-amqp**: For integrating with RabbitMQ.
- **spring-boot-starter-data-redis**: For integrating with Redis.
- **spring-boot-starter-log4j2**: For flexible and performant logging capabilities.

#### Database
- **PostgreSQL**: As the database for storing event data.
- **spring-boot-starter-data-jpa**: For easy data access and manipulation using JPA.

#### Messaging and Caching
- **RabbitMQ**: Enable efficient messaging and communication between services.
- **Redis**: Implement caching to improve performance and scalability.

#### Spring Cloud
- **spring-cloud-starter-config**: For externalized configuration management.
- **spring-cloud-starter-netflix-eureka-client**: For service registry and discovery with Netflix Eureka.
- **spring-cloud-starter-openfeign**: For writing declarative REST clients.
- **spring-cloud-starter-circuitbreaker-resilience4j**: For adding circuit breakers and other resilience patterns.

#### Observability and Monitoring
- **Micrometer**: Gain insights and metrics.
- **micrometer-tracing**: For application tracing.
- **micrometer-tracing-bridge-brave**: For bridging Micrometer and Brave.
- **zipkin-reporter-brave**: For reporting tracing data to Zipkin.
- **feign-micrometer**: For integrating Micrometer with Feign clients.
- **Papertrail**: Centralize and monitor your logs.

### Components
-  **[Event microservice](https://github.com/virtushawk/boxapp-event)** - Core service. Provides all related logic to event domain.
-  **[User microservice](https://github.com/virtushawk/boxapp-user)** - Core service. Provides all related logic to user domain.
-  **[Configuration microservice](https://github.com/virtushawk/boxapp-confsvr)** - Configuration service that reads services configuration from github repository and injects into them on startup
-  **[Service discovery client](https://github.com/virtushawk/boxapp-eureka-client)** Service discovery client.

### Getting Started

#### Running with Docker Compose

This project can be run using Docker Compose to set up the entire microservices ecosystem.

1. **Clone and build Components**:

   Clone all components and build images for them. You can find Dockerfile in every repository and you just create a image for every component.

   For configuration service you will need to provide your own repository where data can be fetched from. Take a look at readme file in repository

2. **Clone docker compose file**:

   You can use provided [docker-compose](docker-compose.yml) to run whole microservice system. You'll need to change a couple of things first.

   1. PAPERTRAIL - if you want to use papertrail you will need to provide you own instance url in
      `syslog://logs5.papertrailapp.com:39580`
   2. KEYCLOAK - In keycloak you will need to create `keycloak` db and provide password to access it `- DB_PASSWORD=2745839`. You will also need to configure keycloak server realm, check [keycloak-configuration](keycloak-configuration)
   3. POSTGRES - you will need to create `user` and `event` db and provide password to access one. You can check core component's repositories to find information how to do this
      for `volumes:postgres_data` you can use local driver, I used external because I had an instance before
    
3. **Clone docker compose file**:

   Now you can run docker compose and test your system!

### License

This project is open-source and available under the [MIT License](LICENSE).
