# Debugging

This image is used to use php xdebug to enable remote debugging. Attetion the ip adresses are assumed to be:

*   172.17.0.1 the host
*   172.17.0.2 the running docker image

if these are not true to you you will have to adapt the settings ind the Dockerfile.

## eclipse-php
   
Install eclipse with php support http://www.eclipse.org/downloads/packages/eclipse-php-developers/mars2

## checkout

Clone folowing repositories:

*   https://github.com/VereinGegenTierfabriken/ocdocker.git
*   https://github.com/VereinGegenTierfabriken/ocdocker-xdebug.git
*   https://github.com/VereinGegenTierfabriken/oc-server3.git

import them all as general projects. and configure oc-server3 to enable php-support.

## configure a server

in the eclipse settings go to PHP/Server and add a default server.

### Tab Server:

* base url: http://172.17.0.2

### Tab Debugger:

* Debugger: Xdebug
* port: 9000

### Tab path mapping:

* "/" -> "/oc-server3/htdocs"
* "/oc" -> "/oc-server3"

## start debuging

### start docker

download the image if you do not have it already

    docker pull  ritchiegithub/ocdocker-xdebug

start the docker image

    docker run -d -p 80:80 -p 3306:3306  ritchiegithub/ocdocker-xdebug

### register a new user

start debugging launch and click on register, and fill out the form. 
jetzt per browser nach localhost und neu registieren.

## get the resistration code

connect to a docker shell

    docker exec -it your-docker-image-hash bash

there should be s spooled email somewhere:

    cat /var/spool/nullmailer/queue/1471780804.395
   
the numbers vary of cource ;-) now decode the base64 text inside. There you find the activation link:

    http://172.17.0.2/a.php?e=ritchie%40gmx.at&c=C3CB19348B418

Now you are registerd and should be able to login, if the current issue would not prohibit it. See  
oc-server-issue-report.txt

....

