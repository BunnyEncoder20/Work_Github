# Nginx

- The basic web model is teh client-server model.
- Even today when a client machine requests a resource, a server machine has to use a software to identify where the resource is stored and send it back.
- This server software for majority of the websites is **Nginx**
    - **Nginx** is a high performace server software, a piece of software which handles HTTP requests on the server machine.
    - **Nginx** is also a proxy server. Being a proxy server it comes with many functionality. Some of the most popular uses is:
        - a **load balancer**: It can proxy the requests into multiple backend systems to balance the incoming load and improve performance
        - **Caching**: is a core feature of Nginx. It cache resp from backend server for freq accessed resources. Copies or stores the resources temp, to improve performance.
        - **Security**: instead of directly making our enterprize servers publicly accessilble, we only expose the Nginx Proxy server to public internet. This means only one server needs majority of the security and remaining multiple servers will remain secure.
        - **Compression & Segmentation**: provides 2 way compression (both on client and server sides) for large image and video files to reduce bandwidth usage and improve load times. It also can perform segmentation or streaming of smaller chunks of data

![nginx proxy functionalities](./assests/nginx_01.png)

**NOTE:** Proxy means to use on behalf of another. So a proxy server is basically a intermediateery server that forwards the client's requests to another server


## Load Balancer
Few of the load balancing methods include:
1. Least Connections: route traffic to the server with the least number of connections
2. Round Robbin: distributes client traffic in sequential, cyclical manner to each server in the group

## Security
1. Consolidated security
2. Minimum expose
3. Centralized Access control
4. Centralized Logging and monitoring

Not only that, we can take additional security methods with the proxy server:

### Encrypted Communications (SSL/Termiation Offloading)
- Nginx can handle **SSL/TLS** encryption and decryption. Even if aatacker, intercepts the message/packets, he cannot read it.
- The proxy server doesn't itself decryption the message, it passes it to the server where it is finally decrypted (remember that the proxy servers are usually exposed to the internet)
- The Proxy server can also be configured to accept only encrypted messages (**Enforce HTTPS**) and deny any non-encrypted requests.

---

## Nginx Configuration
- a main config file is typically named nginx.config and located in the "./etc/nginx/" dir
- uses it's own syntax in form of `Directives` and `Blocks`
- The configuration is:
    - straightforward
    - granular
- this is also where u can config your server's default behaviour. (Either a web or proxy server)
- A very basic server config for nginx would look like this:
```bash
server {
    listen 80;
    server_name example.com www.example.com;
    location / {
        root /var/www/example.com;
        index index.html index.htm;
    }
}
```
- This one:
    - example of web server setup which servers the web pages from itself
    - `location`directives defines how the server should handle the incoming req and specify where the resources are located. Either this this machine or another server machine.
- **NOTE:** That communicating on the HTTP port is insecure and we should always redirect the incoming traffic to encrypted comm lines.
- A more proper example would be:
```bash
server {
    listen 80 ;
    server_name example.com www.example.com;

    # Redirect all HTTP requests to HTTPS
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    server_name example.com www.example.com;

    # SSL Configuration
    ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;

    # Security Headers
    add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
    #...

    location / {
    root /var/www/example.com;
    index index.html index.htm;
}
```
- This one:
    - First server block redirects all incoming HTTP traffic to HTTPS
    - Second server block servers the files over HTTPS with secure SSL/TLS configured.

### Load Balancer Config
- We can even add configuration for load balancing
```bash
http
{
    upstream myappl {
        server srv1.example.com;
        server srv2.example.com;
        server srv3.example.com;
    }

    server {
        listen 80;
        location / {
            proxy_pass http://myappl;
        }
    }
}
```
- In the above example there will be 3 instances of the same server running through srv1-srv3.
- We can further configure which load balancing algorithm to be used as (defaults to round robin):
```bash
upstream myappl {
    Least_conn;     # load balancing algo
    server srvl.example.com;
    server srv2.example.com;
    server srv3.example.com;
}
```

### Caching Config
- We can also configure the caching of the server with great detail as follows:
```bash
http {
    #...
    proxy_cache_path /data/nginx/cache keys_zone=mycache: 10m;
}
```

- Then include the proxy_cache directive in the context (protocol type, virtual server, or location) for which you want to cache server responses, specifying the zone name defined by the keys_zone parameter to the proxy_cache_path directive (in this case, mycache):
```bash
http {
    # ...
    proxy_cache_path /data/nginx/cache keys_zone=mycache: 10m;
    server {
        proxy_cache mycache;
        location / {
            proxy_pass http://localhost:8000;
        }
    }
}
```

---

# Nginx in Kubernettes

- Cause Nginx is so popular and useful, it is the ingress controller (specialized proxy server / load balancer for managing ingress (incoming) req in kubernettes)
- It handles the routing to the appropriate services based on rules defined in the Ingress resource.
![nginx as ingress controller for k8s](./assests/nginx_03.png)
- It actually lives inside the cluster so it cannot be accessed from outside
- It is usually a cloud Load Balanceer which is exposed to the public
- For the security of the cluster, it's parts (nginx ingress controller here) should never be accessible to the public directly
- It is only used after the Cloud load balancer directs traffic to it. It ingress controller will then intelligently (sending reqs to specified microservices) route the traffic to the appropriate services based on the defined rules.

---

# Alternatives

- Apache Server is also basically the same server software, which has been around for longer.
- It's advntages:
    - Highly customizable and extensible
    - good choice for dynamic content handling and legacy support
- Even though Apache Server dominated before Nginx (2004), Nginx quickly took over because:
    - it was faster and more lightweight
    - better suited for high performace envs and static content
    - Simplier configuration AND
    - Much more widely popular in the container world.
