+++
comments = true
date = "2016-02-03T19:37:18+01:00"
description = "Learn how to redirect HTTP to HTTPS and any subdomain to a single HTTPS subdomain."
draft = false
image = "images/post/default-post.png"
tags = ["nginx", "ssl"]
title = "Nginx: Redirect any subdomain http or https to a single subdomain"
+++

{{< figure src="/images/post/logo/nginx.png" class="img-responsive center-block" alt="Nginx" >}}

Today I had a use case where I wanted to redirect any subdomain at any scheme (http or https) to a single https subdomain https://ping.flenny.net.

http://blog.flenny.net should redirect to https://ping.flenny.net<br>
https://www.flenny.net should redirect to https://ping.flenny.net

In order to redirect both schemes (http and https) to a single subdomain you have to setup two `server` blocks. The first one catches all the traffic to any scheme (`listen 80;  listen 443`) at any subdomain (`*.flenny.net`). The second one listens only on port `443` and the specific subdomain `ping.flenny.net`.

~~~nginx
	server {
		listen 80;
		listen 443 ssl;
		server_name *.flenny.net;
		return 301 https://ping.flenny.net$request_uri;
	}
	
	server {
		listen 443 default ssl;
		server_name ping.flenny.net;
		
		root /var/www/flenny;
		index index.html index.htm;
	
		ssl on;
		ssl_certificate			path/to/ssl.crt;
		ssl_certificate_key		path/to/ssl.key;
				
		location / {
			proxy_pass https://x.y.z;
		}
	}
~~~

For a specific port you can only have one ssl configuration section (`ssl_certificate`, `ssl_certificate_key`). As shown in the example above use the keyword `default` to flag the appropriate `server` block.

**Important:** In order to properly redirect e.g. https://blog.flenny.net to https://ping.flenny.net you must have a valid ssl certificate for both subdomains.

A full example of a working Nginx configuration you can get <a href="https://gist.github.com/flenny/de4b6ab465ed5b1c6886" target="_blank">here</a>.