# Install Homebrew

Don't have homebrew installed yet? See http://mxcl.github.com/homebrew/

# Install NGINX

Install nginx using homebrew.

    brew install nginx

Follow the screen instructions to load the plist launchctl file from brew and have nginx start

Backup the original nginx config file.

    cd /usr/local/etc/nginx
    cp nginx.conf nginx.conf.orig

Replace /usr/local/etc/nginx/nginx.conf with the following.

    #user  nobody;
    worker_processes  1;

    #error_log  logs/error.log;
    #error_log  logs/error.log  notice;
    #error_log  logs/error.log  info;
    
    #pid        logs/nginx.pid;
    
    
    events {
        worker_connections  1024;
    }
    
    
    http  {
        include       mime.types;
        default_type  application/octet-stream;
    
        #access_log  logs/access.log  main;
    
        sendfile        on;
        #tcp_nopush     on;

        #keepalive_timeout  0;
        keepalive_timeout  65;

        #gzip  on;

        include /Users/oconnor/Sites/configs/nginx/sites-enabled/*;

     }

On the site-enabled/mirosubs.conf, something like:



    server {
     listen  8080;
     server_name mirosubsmedia.example.com;

      location /{
            root /Users/arthur/Documents/projects/unisubs/mirosubs/media;
    		autoindex on;
      }

    }

Of course, add mirosubsmedia to your hosts, restart nginx