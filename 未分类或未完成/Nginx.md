# Nginx

- https://www.nginx.org.cn/article/detail/545
- https://tengine.taobao.org/book/index.html
- https://zxuqian.cn/install-nginx-on-ubuntu-20-04/#4-%E6%94%BE%E9%80%9A%E9%98%B2%E7%81%AB%E5%A2%99%E7%AB%AF%E5%8F%A3
- nginx中文官方文档https://wizardforcel.gitbooks.io/nginx-doc/content/index.html
- https://wizardforcel.gitbooks.io/nginx-doc/content/Text/6.3_nginx_ubuntu.html

## nginx指令





## nginx.conf

主配置：`/etc/nginx/nginx.conf`

新增配置位置：`cat /etc/nginx/conf.d/default.conf`

```nginx
events {
		
}

http {

	include /etc/nginx/mime.types;
	
	server {
		listen 80;
		server_name localhost;
		root /var/www/localhost;
		index myIndex.html;
		
		location / {
			root /var/www/localhost;
		}
		# 完全匹配
		location = /app/index.html {
			root /var/www/localhost;
		}
		# 正则表达式
		location ~ /app/app[1-3].html {
			root /var/www/localhost;
		}
	}
}
```

检查配置文件，然后重载`nginx -t && nginx -s reload`

停止`nginx -s stop`

请求`curl -i localhost`



创建存放网页文件的文件夹：`mkdir /var/www/localhost`



### 编辑自己的配置

`cp /etc/nginx/conf.d/default.conf /etc/nginx/conf.d/yourdomain.conf`

```nginx
```



## Vitepress & Nginx配置

```nginx
server {
    gzip on;
    gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

    listen 80;
    server_name _;
    index index.html;

    location / {
        # content location
        root /app;

        # exact matches -> reverse clean urls -> folders -> not found
        try_files $uri $uri.html $uri/ =404;

        # non existent pages
        error_page 404 /404.html;

        # a folder without index.html raises 403 in this setup
        error_page 403 /404.html;

        # adjust caching headers
        # files in the assets folder have hashes filenames
        location ~* ^/assets/ {
            expires 1y;
            add_header Cache-Control "public, immutable";
        }
    }
}
```

## 安装配置Nginx

> 访问时，不要使用https，因为还没有配置，这样访问会失败

## blessing-skin nginx配置

```nginx
server {
        listen       80;
        server_name  localhost;
        root /var/www/blessing-skin/public;


        location / {
            index  index.php index.html index.htm;
        try_files $uri $uri/ /index.php?$query_string;
        }

        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }


        # php-fpm配置
        location ~ [^/]\.php(/|$){
            # try_files $uri =404;
            fastcgi_pass  127.0.0.1:9000;
            include fastcgi.conf;
            fastcgi_index  index.php;
            fastcgi_param  SCRIPT_FILENAME  $document_root/$fastcgi_script_name;
        }
    }
```

