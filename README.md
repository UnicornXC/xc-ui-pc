## 项目的门户主界面

- 直接下载之后部署

### nginx 配置

```sh
worker_processes  1;

events {
    worker_connections  1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;

    sendfile        on;
    keepalive_timeout  65;

    server{
	      listen       80;
	      server_name  www.xuecheng.com;
	      ssi on;
	      ssi_silent_errors on;
	      location / {
		      alias   /path/to/xc-ui-pc/;
		      index  index.html;
	      }
    }
}
```
