[Return to Table of Contents](README.md)
### Nginx sits in front of other web services and acts as a gatekeeper and reverse proxy.

#### Copy the contents of nginx-jelastic.conf to:
conf.d/reverse-proxy.conf

#### Comment out:
`#include /etc/nginx/nginx-jelastic.conf;`

#### Add:
`include /etc/nginx/conf.d/*.conf;`

### See reverse-proxy.conf for the full configuration file.

#### Edit /etc/nginx/conf.d/reverse-proxy.conf:
```
client_max_body_size 500m
large_client_header_buffers 4 32k
```

### Force HTTPS:
```
server {
    listen      *:80;
    server_name sparql.vanderbilt.edu localhost;
    return 301 https://$server_name$request_uri;
}
```

### Set up basic authentication:
See [authentication-setup.md](authentication-setup.md).
