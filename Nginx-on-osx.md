## Install Homebrew

Don't have homebrew installed yet? See http://mxcl.github.com/homebrew/

## Install NGINX

Install nginx using homebrew.

    brew install nginx

Follow the screen instructions to load the plist launchctl file from brew and have nginx start

Backup the original nginx config file.

    cd /usr/local/etc/nginx
    cp nginx.conf nginx.conf.orig

Replace /usr/local/etc/nginx/nginx.conf with the following. Swap out `/Users/adamduston/dev/mirosubs/media` with your local directory.

    #user  nobody;
    worker_processes  1;
    
    #error_log  logs/error.log;
    #error_log  logs/error.log  notice;
    #error_log  logs/error.log  info;
    
    #pid        logs/nginx.pid;
    
    events {
        worker_connections  1024;
    }
    
    http {
        include       mime.types;
        default_type  application/octet-stream;
    
        #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
        #                  '$status $body_bytes_sent "$http_referer" '
        #                  '"$http_user_agent" "$http_x_forwarded_for"';
    
        #access_log  logs/access.log  main;
    
        sendfile        on;
        #tcp_nopush     on;
    
        #keepalive_timeout  0;
        keepalive_timeout  65;
    
        #gzip  on;
    
        server {
            listen       8888;
            server_name  mirosubsmedia.example.com;
    
            location / {
                root   /Users/adamduston/dev/mirosubs/media
                autoindex on;
            }
        }
    }

## Alter /etc/conf/hosts

Add mirosubsmedia.example.com to your hosts, restart nginx

## Alter your settings_local file

Add to settings_local.py:

    MEDIA_URL = 'http://mirosubsmedia.example.com'