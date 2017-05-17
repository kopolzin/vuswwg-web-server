### Nginx sits in front of the web services and acts as a gatekeeper and reverse proxy.

#### Copy the contents of nginx-jelastic.conf to:
conf.d/reverse-proxy.conf

#### Comment out:
`#include /etc/nginx/nginx-jelastic.conf;`

#### Add:
`include /etc/nginx/conf.d/*.conf;`

### See reverse-proxy.conf for the full configuration file

#### Edit /etc/nginx/conf.d/reverse-proxy.conf
`client_max_body_size 500m`

### In nginx.conf, force https:
```
server {
    listen      80;
    server_name signup.mysite.com;
    return 301 https://$server_name$request_uri;
}
```

## Create password file:
### If the 'which htpasswd' command returns empty, install apache2-utils
`htpasswd -c /etc/nginx/conf.d/.htpasswd username1`
#### prompted for password
## subsequent users (prompted for password after hitting return):#
`htpasswd /etc/nginx/.htpasswd username2`

### alternatively, use OpenSSL
`sudo sh -c "echo -n 'usernamehere:' >> /etc/nginx/.htpasswd"`

### Next, add an encrypted password entry for the username by typing:
`sudo sh -c "openssl passwd -apr1 >> /etc/nginx/.htpasswd"`

### Add authorized users to /etc/nginx/conf.d/.htpasswd
`usernamehere:$apr1$somethingsomething`

