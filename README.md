# mono-server-setup

Example configuration files for setting up a Nginx server to forward request to a Mono ASP.NET site via FastCGI and Mono's `fastcgi-mono-server4
![Mono Server Setup Diagram](https://raw.githubusercontent.com/shturm/mono-server-setup/master/mono-server-setup.png)

## Files

* `etc/nginx/fastcgi_params` - Nginx configuration for FastCGI protocol. For each request, it explains which values should be forwarded to FastCGI and under what environment names. Variables starting with `$` are Nginx variables. E.g. `$remote_addr` will be replaced by the IP address of the client sending the HTTP request.
* `etc/mono/fastcgi/thesite.com.webapp` - Virtual host for Mono as an ASP.NET site. Essentially serves same purpose Apache/Nginx virtual host configuration, but Mono has separate configuration for this. Could be placed anywhere and can be omitted, because it's values can be specified as parameters of the fastcgi-mono-server. However it's recommended to have a folder with all you Mono virtual hosts.
*  `etc/nginx/sites-available/thesite.com` - Nginx virtual host for the site. It tells Nginx to forward requests matching specific domain/port to the Mono FastCGI server via FastCGI protocol.
* `fastcgi-server.sh` - Command line to start the Mono FastCGI server - `fastcgi-mono-server`. It should know which applications it should host (in this setup it's via etc/mono/fastcgi/thesite.com.webapp configuration) and on which port it should listen for FastCGI requests (sent from Nginx for each request it receives).
