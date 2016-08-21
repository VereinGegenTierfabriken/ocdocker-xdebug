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

just launch the provided launch and a browser window should open ind debug state.
