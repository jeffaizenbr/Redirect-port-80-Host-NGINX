# Example, redirect the address "192.168.122.14:10000" to localhost port default 80 


# 1 - Install EPEL release 

```bash
yum install epel-release
```

# 2 - Install NGINX 

```bash
yum install nginx
```

# 3 - create e file in /etc/nginx/conf.d/filename.conf

```bash
server {
    listen 80;

    server_name localhost;

    #auth_basic "Restricted Access";
    #auth_basic_user_file /etc/nginx/htpasswd.users;

    location / {
        proxy_pass http://localhost:10000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```
