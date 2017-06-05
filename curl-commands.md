[Return to Table of Contents](README.md)
#### Return a single query result using GET
`curl -v -L -G  'https://sparql.vanderbilt.edu/bg/sparql' --data-urlencode 'query=SELECT * { ?s ?p ?o } LIMIT 1'`

#### Return a single query result using POST -- requires authentication
`curl -u yourusername:yourpassword -v -L -X POST 'https://sparql.vanderbilt.edu/bg/sparql' --data-urlencode 'query=SELECT * { ?s ?p ?o } LIMIT 1'`

#### Drop all records from the database
`curl -u yourusername:yourpassword -X POST https://sparql.vanderbilt.edu/bg/sparql --data-urlencode 'update=DROP ALL;'`

#### Insert RDF into database from a file (example: streamteam.rdf) on user's computer
`curl -u yourusername:yourpassword --header 'Content-Type:application/rdf+xml' -X POST --data-binary '@streamteam.rdf' https://sparql.vanderbilt.edu/bg/sparql`

#### Insert RDF from URL using --data-urlencode
`curl -u yourusername:yourpassword -X POST https://sparql.vanderbilt.edu/bg/sparql --data-urlencode 'update=LOAD <http://bioimages.vanderbilt.edu/index.rdf>;'`

#### Insert RDF from URL using --data-binary
`curl -u yourusername:yourpassword -X POST https://sparql.vanderbilt.edu/bg/sparql --data-binary 'uri=http://bioimages.vanderbilt.edu/index.rdf'`

#### Load data from RDF file (example: images.rdf) already on the web server
`curl -u yourusername:yourpassword --header 'Content-Type:application/rdf+xml' -X POST --data-binary '@images.rdf' https://sparql.vanderbilt.edu/bg/sparql`

#### Load data from gzipped RDF file (example: images.rdf.gz) already on the web server
`curl -u yourusername:yourpassword -X POST --data-urlencode 'update=LOAD <file:///opt/tomcat/temp/organisms.rdf.gz>' https://sparql.vanderbilt.edu/bg/sparql`
