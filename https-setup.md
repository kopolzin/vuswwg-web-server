[Return to Table of Contents](README.md)

### HTTPS
Jelastic provides instructions for setting up a free Let's Encrypt SSL certificate to enable HTTPS on your site. A prerequisite is to create a DNS A record pointing your preferred subdomain to the public IP address of your Jelastic server's Nginx instance, which is outside the scope of this tutorial.

http://blog.jelastic.com/2017/02/01/free-ssl-certificates-with-lets-encrypt/

Following those instructions will install SSL certificates on your Nginx server. Next you must modify your Nginx configuration files to point to those certificates.

See [nginx-example.conf](nginx-example.conf) for an example of a complete configuration with HTTPS set up. If installing Let's Encrypt within Jelastic created the file `/etc/nginx/conf.d/ssl.conf` you can safely delete it.

### Explanation of several configuration settings

#### Mozilla provides a web server configuration generator
It is particularly useful for selecting SSL ciphers.<br>
https://mozilla.github.io/server-side-tls/ssl-config-generator/

#### To force HTTPS within Nginx:
```
server {
    listen      80;
    server_name sparql.vanderbilt.edu;
    return 301  https://$server_name$request_uri;
}
```

#### Authentication
We want to protect changes to Blazegraph data by requiring a username and password. This is accomplished by using basic authentication within Nginx. Here is an example within a location block.

```
limit_except GET {
    auth_basic      "Authentication required";
    auth_basic_user_file /etc/nginx/conf.d/.htpasswd;
}
```

In this example `limit_except GET` means that all HTTP methods other than GET, such as POST and DELETE, will require authentication. `auth_basic` warns unauthenticated users and can be set to any string. `auth_basic_user_file` is the location of the username and encrypted password file. See [authentication-setup.md](authentication-setup.md) for more information.
