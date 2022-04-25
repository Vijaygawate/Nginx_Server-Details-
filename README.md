# Nginx_Server-Details-

**Compariason between Apache and Nginx Server:::::**
1. Nginx is high performance with less resources.
2. Test based config files with first and third party module support.

Nginx works as:
    - A web server 
    - A reverse proxy server 
    - A proxy server for mail server 

3. Apache works on prefork model while nginx works on worker model 

Meaninng of Prefork model and Worker model 
**Prefork Model: **: In Apache if we have 3 diff files with diff extensions foe eg .php .py .txt then Apache will open 3 diff connections to process this files 

**Worker Model **: In nginx worker model , if we have any no of files with all diff extensions , nginx will open only one connection to process the requests, and that is the reason why nginx is fast and have high performance 
=======================================================================================================================================================
**Installation of Nginx on ubuntu:::::**
#apt-get update 
#apt-get install nginx -y 
#nginx -v                     @@@@(to check the version of nginx server)
#ps fax | grep nginx          @@@@(to check the what are the process are running related to nginx)

Now, To check if Nginx is working or not 
<public_ip of nginx server> paste it on browser 

_Default port for nginx is 80_

#netstat -tunlp.             @@@@(to nginx working on which port)

#rpm -qa | grep nginx.       @@@@(to check any packages installed on sysytem)
#service nginx start         @@@@(to start the nginx server)
#systemctl enable nginx.service
#systemctl status nginx
=======================================================================================================================================================
**Adding Nginx as a serviec in Ubuntu**
Our Nginx is running , to stop the nginx service 
#nginx -s stop 

Go to https://www.nginx.com/resources/wiki/start/topics/examples/initscripts/
select NGINX systemd service file

Now, craete the file with mentioned path on ubuntu server 
#vi /lib/systemd/system/nginx.service
and paste the file content as
====== 
[Unit]
Description=The NGINX HTTP and reverse proxy server
After=syslog.target network-online.target remote-fs.target nss-lookup.target
Wants=network-online.target

[Service]
Type=forking
PIDFile=/var/run/nginx.pid
ExecStartPre=/usr/bin/nginx -t
ExecStart=/usr/bin/nginx
ExecReload=/usr/bin/nginx -s reload
ExecStop=/bin/kill -s QUIT $MAINPID
PrivateTmp=true

[Install]
WantedBy=multi-user.target
=====
Now , start the nginx with bwlow command 

#systemctl start nginx 
=======================================================================================================================================================
**How to create virtual host in Nginx**
