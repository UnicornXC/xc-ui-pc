## 项目的门户主界面

- 直接下载之后部署

### nginx 配置

- 注意开启服务端包含项目 `ssi` 

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
	      server_name  www.xconline.edu;

        # 服务端包含技术
	      ssi on;
	      ssi_silent_errors on;

	      location / {
		      alias   /path/to/xc-ui-pc/;
		      index  index.html;
	      }
    }
}
```

### 域名访问

- 如果需要使用域名访问，则修改 `/etc/hosts` 文件

```sh
127.0.0.0  www.xconline.edu
```
