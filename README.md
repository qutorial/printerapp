# Simple PDF file printer app


Example nginx configuration:

```
server {
	listen 80 default_server;
	listen [::]:80 default_server;

        # Put the app here
	root /var/www/html;
	index index.html;
	server_name _;

        include /etc/nginx/fcgiwrap.conf;

        # Max PDF file size
        client_max_body_size 15M;

	location / {
		index	index.html;
		fastcgi_index	index.html;
		fastcgi_pass  unix:/var/run/fcgiwrap.socket;
	        include /etc/nginx/fastcgi_params;
	        fastcgi_param SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        }

}
```

Installation of additional packages:

```apt-get install lpr lptools fcgiwrap```

