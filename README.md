## Python 3.11.6

## Node 18.18.0

## npm 10.2.4


# to start application run following command

- in terminal 1 npm run dev
- in terminal 2 python manage.py runserver



https://dev.to/zachtylr21/how-to-serve-a-react-single-page-app-with-django-1a1l#:~:text=Now%20that%20your%20frontend%20app,%2Ffrontend%2F%20create%20an%20index.
https://www.digitalocean.com/community/tutorials/how-to-set-up-django-with-postgres-nginx-and-gunicorn-on-ubuntu-22-04


while deploying django application in ec2
Copy your project static files to /var/www/static

# cp -r /project/static /var/www/static
Point nginx to proper directory

# sudo nano /etc/nginx/sites-available/default

server {
        listen 80 default_server;
        listen [::]:80 default_server;

        server_name _;

        location /static/ {
                root /var/www;
        }

        location / {
                include proxy_params;
                proxy_pass http://unix:/run/gunicorn.sock;
        }

}
Test nginx config and reload

# sudo nginx -t
# sudo systemctl reload nginx
