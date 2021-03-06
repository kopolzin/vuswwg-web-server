# vuswwg-web-server
Instructions for setting up the Vanderbilt University Semantic Web Working Group (VUSWWG) web server.

## Overview
The VUSWWG provides several public web services, including access to a Blazegraph SPARQL endpoint and a BaseX XML database. These services are run behind an Nginx web server which acts as a reverse proxy and provides authentation for secure write access and rate limiting to API resources.

\[ users \] \<=====\> \[ publicly-accessible Nginx \] \<=====\> \[ private Blazegraph/BaseX \]

[Nginx setup](nginx-setup.md)

[Basic authentication setup](authentication-setup.md)

[Blazegraph setup](blazegraph-setup.md)

[HTTPS setup](https-setup.md)

[Example CURL commands](curl-commands.md)
