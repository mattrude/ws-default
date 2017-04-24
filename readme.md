# Default website

The idea of this site is to be a simple, none-reveling, page to be put as the servers default page.

## Nginx config
Below is the entry for `nginx.conf`, this entry must be the top most `server` entry:

    server {
        listen 80 default_server;
        listen [::]:80 ipv6only=on;
        root /var/www/html;
        
        error_page 404 =410 /gone.html;
        error_page 410 /gone.html;
        error_log off;
        
        location /readme.md {
            deny all;
        }
        
        location /_config.xml {
            deny all;
        }
    }
