# nginx-streams
Nginx streams on ec2


# Install Nginx on ec2

```bash

amazon-linux-extras list | grep nginx
amazon-linux-extras enable nginx1
yum clean metadata
yum -y install nginx
yum -y install nginx-mod-stream
 
```

# nginx.conf

```bash
# Load dynamic modules. See /usr/share/doc/nginx/README.dynamic.
include /usr/share/nginx/modules/*.conf;
 
events {
    worker_connections 1024;
}
 
stream {
    upstream app_node {
        server 127.0.0.1:4000;
    }
 
    server {
        listen 8080;
        proxy_pass app_node;
    }
}

```

# Test configuration

```bash
nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful

```
