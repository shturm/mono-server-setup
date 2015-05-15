# /etc/nginx/sites-available/monoserver - nginx virtualhost. Names don't matter
server {
	listen 8081;

	server_name localhost;
	access_log   /var/log/nginx/aspnet.access.log;
	error_log   /var/log/nginx/aspnet.error.log;

	location / {

		root /home/alx/src/daidakaram/monoserver/webclient;
		index index.html index.htm default.aspx Default.aspx;
		fastcgi_index Default.aspx;
		fastcgi_pass 127.0.0.1:9000;
		include /etc/nginx/fastcgi_params;
		# try_files $uri $uri/ =404;
	}
}