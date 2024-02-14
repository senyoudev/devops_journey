## Containers for Developement

Containers are used in Development to ensure that the software runs consistently across different environments.

## Containers for Testing

# How do containers work in testing?

Containers in testing are used to do integration testing, unit testing, and end-to-end testing. Containers are used to ensure that the software runs consistently across different environments.

## Containers for Packaging

Containers are used for packaging software in a format that can run consistently on any platform. 

Why ? 
- Packaging is fiddly and time-consuming
- Packaging is error-prone
- Packaging is not repeatable
- Packaging is not portable
- Packaging is not scalable
- Packaging is not secure

so when we use containers for packaging we can ensure that the software runs consistently across different environments.

## Docker-compose Example 

Docker-compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application's services. Then, with a single command, you create and start all the services from your configuration.

```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/code
    environment:
      FLASK_ENV: development
  redis:
    image: "redis:alpine"
```