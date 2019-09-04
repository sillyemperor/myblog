Title: 用systemctl管理nginx服务实现自动启动
Date: 2019-06-04
Category: Nginx
Tags: nignx,systemctl

创建文件

/lib/systemd/system/nginx.service

[Unit]

Description=The NGINX HTTP and reverse proxy server

After=syslog.target network.target remote-fs.target nss-lookup.target

[Service]

Type=forking

PIDFile=/run/nginx.pid

ExecStartPre=/usr/sbin/nginx -t

ExecStart=/usr/sbin/nginx

ExecReload=/usr/sbin/nginx -s reload

ExecStop=/bin/kill -s QUIT $MAINPID

PrivateTmp=true

[Install]

WantedBy=multi-user.target


启动项目

systemctl enable nginx.service

systemctl start nginx.service


查看项目状态

systemctl status nginx.service


Reload项目

systemctl reload nginx.service


Restart项目

systemctl restart nginx.service