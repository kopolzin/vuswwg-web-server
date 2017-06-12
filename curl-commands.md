[Return to Table of Contents](README.md)

The definitive SPARQL API documentation is at Blazegraph's [wiki](https://wiki.blazegraph.com/wiki/index.php/REST_API). The following are example queries to get started.

#### Return a single query result using GET
`curl -v -L -G  'https://sparql.vanderbilt.edu/sparql' --data-urlencode 'query=SELECT * { ?s ?p ?o } LIMIT 1'`

#### Return a single query result using POST -- requires authentication
`curl -u yourusername:yourpassword -v -L -X POST 'https://sparql.vanderbilt.edu/sparql' --data-urlencode 'query=SELECT * { ?s ?p ?o } LIMIT 1'`

#### Drop all records from the database
`curl -u yourusername:yourpassword -X POST https://sparql.vanderbilt.edu/sparql --data-urlencode 'update=DROP ALL;'`

#### Insert RDF from URL using --data-urlencode
`curl -u yourusername:yourpassword -X POST https://sparql.vanderbilt.edu/sparql --data-urlencode 'update=LOAD <http://bioimages.vanderbilt.edu/index.rdf>;'`

#### Insert RDF from URL using --data-binary
`curl -u yourusername:yourpassword -X POST https://sparql.vanderbilt.edu/sparql --data-binary 'uri=http://bioimages.vanderbilt.edu/index.rdf'`

#### Load data from RDF file (example: images.rdf) already on the web server in the default directory (/opt/tomcat/temp/)
`curl -u yourusername:yourpassword --header 'Content-Type:application/rdf+xml' -X POST --data-binary '@images.rdf' https://sparql.vanderbilt.edu/sparql`

#### Load data from gzipped RDF file (example: images.rdf.gz) already on the web server
`curl -u yourusername:yourpassword -X POST --data-urlencode 'update=LOAD <file:///opt/tomcat/temp/organisms.rdf.gz>' https://sparql.vanderbilt.edu/sparql`
