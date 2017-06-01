[Return to Table of Contents](README.md)
#### Drop all records from the database
`curl -u yourusername:yourpassword -X POST http://vuswwg.jelastic.servint.net/bg/sparql --data-urlencode 'update=DROP ALL;'`

#### Insert RDF into database from a file (example: streamteam.rdf) on user's computer
`curl -u yourusername:yourpassword --header 'Content-Type:application/rdf+xml' -X POST --data-binary '@streamteam.rdf' http://vuswwg.jelastic.servint.net/bg/sparql`

#### Insert RDF from URL using --data-urlencode
`curl -u yourusername:yourpassword -X POST http://vuswwg.jelastic.servint.net/bg/sparql --data-urlencode 'update=LOAD <http://bioimages.vanderbilt.edu/index.rdf>;'`

#### Insert RDF from URL using --data-binary
`curl -u yourusername:yourpassword -X POST http://vuswwg.jelastic.servint.net/bg/sparql --data-binary 'uri=http://bioimages.vanderbilt.edu/index.rdf'`

#### Load data from RDF file (example: images.rdf) already on the web server
`curl -u yourusername:yourpassword --header 'Content-Type:application/rdf+xml' -X POST --data-binary '@images.rdf' http://vuswwg.jelastic.servint.net/bg/sparql`

#### Load data from gzipped RDF file (example: images.rdf.gz) already on the web server
`curl -u yourusername:yourpassword -X POST --data-urlencode 'update=LOAD <file:///opt/tomcat/temp/organisms.rdf.gz>' http://vuswwg.jelastic.servint.net/bg/sparql`
