# What is openCRX

[openCRX](https://www.opencrx.org) is an open source CRM solution that meets the needs of organizations requiring multi-functional, 
enterprise-wide coordination of sales generation, sales fulfillment, marketing and service activities to customers, partners,
suppliers or intermediaries.

# How to use this image

## Build this image

    docker build -t opencrx:v5.2.2 .
    
## Run this image

    docker run -d -p 8080:80 -p 8009:8009 -p 8001:8001 --name opencrx opencrx:v5.2.2
    
## Stop container

    docker stop opencrx
    
## Start container

    docker start opencrx
    
## Inspect logs

    docker logs -f opencrx
    docker exec -t -i opencrx /bin/bash
    docker exec -i opencrx cat /home/opencrx/opt/opencrx/apache-tomee-plus-8.0.6/logs/catalina.yyyy-mm-dd.log
    docker cp opencrx:/home/opencrx/opt/opencrx/apache-tomee-plus-8.0.6/logs/catalina.yyyy-mm-dd.log .

# How to extend this image

Here is an example of a custom Dockerfile which replaces the default tomee.xml by a custom configuration:

    FROM opencrx:v5.2.2
    MAINTAINER demo@opencrx.org
    COPY ./tomee.xml /home/opencrx/opt/opencrx/apache-tomee-plus-8.0.6/conf/
