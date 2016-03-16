+++
comments = true
date = "2016-03-15T14:33:21+01:00"
description = "Learn how to make your website a more secure place with NGINX."
draft = false
image = "images/post/secure-http-headers.png"
slug = "secure-your-website-by-adding-some-http-security-headers-with-nginx"
tags = ["ssl", "nginx", "security"]
title = "Secure your website by adding some HTTP security headers with NGINX"
+++

{{< figure width="190em" height="190em" src="/images/post/secure-http-headers.svg" class="pull-right" alt="A+" >}}

In order to make your site a more secure place, it's recommended to add
some HTTP security headers into your web servers response. Without going to much
into detail here, the aim of this blog post is to give you a basic NGINX configuration.
For more detailed information visit {{% a_blank "Scott Helme's blog" "https://scotthelme.co.uk/" %}}.
He did a pretty good job explaining all different types of HTTP security headers.

## X-Frame-Options ##
`X-Frame-Options` specifies whether your browser allows framing your site
into another site. You can `DENY`, allow only from `SAMEORIGIN` or
`ALLOW-FROM https://a.specific.site.com/`

~~~nginx
add_header X-Frame-Options SAMEORIGIN;
~~~

## X-Content-Type-Options ##
With `nosniff` your browser is enforced to use the content-type declared by
your server. It helps reducing the risk of so-called drive-by downloads.

~~~nginx
add_header X-Content-Type-Options nosniff;
~~~

## X-XSS-Protection ##
`X-XSS-Protection` enables Cross-site scripting (XSS) filter built-in into most browsers.
Although this option is enabled by default, it's recommend to re-enable and hence reduce the risk
in which malicious scripts are injected to your site.

~~~nginx
add_header X-XSS-Protection "1; mode=block";
~~~

## Content-Security-Policy ##
`Content-Security-Policy` defines approved sources your browser may load content from.

~~~nginx
add_header Content-Security-Policy "default-src https:
    data: 'unsafe-inline' 'unsafe-eval';" always;
~~~

## Strict-Transport-Security ##
`Strict-Transport-Security` enforces your browser to use HTTPS over regular HTTP.
Use HTTPS over HTTP everywhere and anytime. Even if it's a simple personal blog.
You can get a free SSL certificate at {{% a_blank "StartCom" "https://www.startssl.com/" %}}.
Not long ago, Google also started favoring HTTPS sites in search results.

~~~nginx
add_header Strict-Transport-Security "max-age=31536000;
    includeSubdomains" always;
~~~

## Public-Key-Pins ##
With `Public-Key-Pins` your able to tell your browser in which identities he should trust.
It protects your site from man-in-the-middle attacks and in case if your certificate authority is compromised.
The easiest way to get your appropriate key-pins is by running a test at
{{% a_blank "SSL LABS" "https://www.ssllabs.com/ssltest/" %}}.
The pins are part of the result.

~~~nginx
add_header Public-Key-Pins 'pin-sha256="xxx"; pin-sha256="yyy";
    pin-sha256="zzz"; max-age=2592000; includeSubDomains' always;
~~~