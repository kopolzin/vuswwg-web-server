[Return to Table of Contents](README.md)
### Nginx sits in front of other web services and acts as a gatekeeper and reverse proxy

### Edit the file `/etc/nginx/nginx.conf`

#### Comment out:
`#include /etc/nginx/nginx-jelastic.conf;`

#### Add:
`include /etc/nginx/conf.d/*.conf;`

### Create and edit file `/etc/nginx/conf.d/reverse-proxy.conf`

#### Copy the contents of `/etc/nginx/nginx-jelastic.conf` into `reverse-proxy.conf`

#### See [nginx-example.conf](nginx-example.conf) for an example of the complete reverse-proxy.conf.

#### Increase the body and header buffer sizes:
```
client_max_body_size 500m
large_client_header_buffers 4 32k
```
#### Set up HTTPS on the Jelastic server:
See [https-setup.md](https-setup.md)

#### Set up basic authentication:
See [authentication-setup.md](authentication-setup.md).
