Changes to the Blazegraph database are protected by basic authentication. This is enabled by modifying two files: one containing a list of usernames and encrypted passwords and the other an Nginx configuration file.

### Encrypted passwords
A file must be created containing usernames and encrypted passwords. Two tools are commonly used to encrypt a password: `htpasswd` or `openssl`. htpasswd can be installed on a Debian-based Linux distribution with:

`apt install apache2-utils`

On Windows one must install the entire [Apache HTTP server](http://httpd.apache.org/docs/current/platform/windows.html#down) package. After installation one can move the htpasswd.exe executable found in the /bin directory elsewhere and then uninstall the server. Alternatively, a Windows user may install the latest Win32 Light version of [OpenSSL](https://slproweb.com/products/Win32OpenSSL.html).

With htpasswd installed, generate a username and encrypted password pair by running the following. You will be prompted for the password.

`htpasswd -n exampleusername`

This will display something like: `exampleusername:$apr1$9BwyqxmD$gS61I4FLtlfR6Vd17osVf1` Copy and paste this into the password file on the Jelastic server. If that file has not been created yet, a fine location is `/etc/nginx/conf.d/.htpasswd`.

If OpenSSL is used instead, encrypt the password with the following command. You will be prompted for the password.

`openssl passwd -apr1`

The output will be something like `$apr1$9BwyqxmD$gS61I4FLtlfR6Vd17osVf1`. You will need to manually add the username and a colon in front of this when copying and pasting into the password file on the Jelastic server so that the end result looks like `exampleusername:$apr1$9BwyqxmD$gS61I4FLtlfR6Vd17osVf1`.

### Configuring Nginx for basic authentication
Now that we have a file containing usernames and encrypted passwords we can tell Nginx where it is located at and under what circumstances to require authentication.

A simple example to require authentication for any request type other than GET:

```
location / {
    limit_except GET {
        auth_basic           "Authentication required";
        auth_basic_user_file /etc/nginx/conf.d/.htpasswd;
    }
    ...
}
```

Reload the Nginx web server after you have finished changing settings.

### Changing passwords or removing users
To change a user's password, generate an encrypted password with htpasswd or openssl as shown above and then replace that user's entry in the password file (e.g. /etc/nginx/conf.d/.htpasswd).

To remove a user's access simply remove their line from the password file.
