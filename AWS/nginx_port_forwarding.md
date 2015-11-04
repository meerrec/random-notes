## nginx for port forwarding

### Issue:
Want to run node app with [pm2](https://github.com/Unitech/pm2) on port 80.

### Solution:
Use Nginx to proxy port 80 to whatever you want

#### Install Nginx
- Mac
```
brew install nginx
```
- Ubuntu
```
sudo apt-get install nginx -y
```

#### Create config
- Mac in /usr/local/etc/nginx/nginx.conf

- Ubuntu in /etc/nginx/sites-enabled/. Disable the default site, `sudo rm /etc/nginx/sites-enabled/default` first.

```
server {
    listen 80;
    server_name your-domain-name.com;
    location / {
        proxy_set_header   X-Real-IP $remote_addr;
        proxy_set_header   Host      $http_host;
        proxy_pass         http://127.0.0.1:2368;
    }
}
```
1. server { - Declares a server block
2. server_name your.domain.com; - Nginx routes work from most specific down to least specific. This directive is used to route the incoming request based on it's hostname header. You can fill in your domain name or not worry about.
3. listen 80; - Specifies what port to accept on. It defaults to 80, so feel free to leave it out.
4. location / { - Declares a location block. This can be used for full routing control. In our case, we are routing everything from the root / on.
5. proxy_set_header X-Real-IP $remote_addr; - The first part of this line is the directive used to add or modify a header of the incoming request that we are proxying off to our app. The second, is the name of the header we are altering / creating. In this case, it is the 'X-Real-IP' header, which is used to identify the IP of the original request. The last part, is an Nginx variable that will hold the IP. It's worth noting that all of these headers are only transmitted internally to your app and not back to the client.
6. proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for; - Similar to the line above, but the difference is the use case of the 'X-Forwarded-For' header. It is a comma separated list of all the proxies the request has been through, starting with $remote_addr as the first one.
7. proxy_set_header Host $http_host; - Yet another header. This contains the requested hostname of the server, e.g. example.com.
8. proxy_set_header X-NginX-Proxy true; - Only used to internally know this request was proxied through Nginx.
9. proxy_pass http://127.0.0.1:2368 - The line that makes the magic happen. This is where our request is going to be handed off to.
10. proxy_redirect off; - This directive is used to rewrite the url of the request. We want to keep ours intact so we turn it off.

#### Start, stop and restart
```
sudo service nginx start/stop/restart
```