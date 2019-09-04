Title: Nginx实现双向认证，直接上脚本，想学习更多的看参考
Date: 2019-06-04
Category: Nginx
Tags: nginx,https,openssl,证书

第一步、创建证书

//创建根证书root

openssl genrsa -des3 -out root.key 4096

openssl req -new -x509 -days 3650 -key root.key -out root.crt


//创建服务器证书server

openssl genrsa -des3 -out server.key 1024
openssl req -new -key server.key -out server.csr 
openssl x509 -req -days 3560 -in server.csr  -CA root.crt  -CAkey root.key -set_serial 01 -out server.crt


//创建乘客端证书client

openssl genrsa -des3 -out client.key 1024
openssl req -new -key client.key -out client.csr 
openssl x509 -req -days 3560 -in client.csr  -CA root.crt  -CAkey root.key -set_serial 01 -out client.crt


第二步、配置服务器

//配置Nginx

server {
        listen       443 ssl;
        server_name  localhost www.test.net;

        ssl on;
        ssl_certificate      /路径/cert/server.crt;
        ssl_certificate_key  /路径/cert/server.key;

        ssl_client_certificate /路径/cert/root.crt;
        ssl_verify_client on;

        location / {
            root   html;
            index  index.html index.htm;
        }
    }

重新启动nginx后，服务器就配置好了。下面说说几种客户端如何访问。


第三步、客户端调用

假设我们的访问链接就是：https://www.test.net。

为了方便使用，将客户端证书与密钥打包。

//打包脚本

openssl pkcs12 -export -clcerts -in client.crt -inkey client.key -out client.p12


//curl

curl -Sv --cert client.p12:client.key的密码  -k https://www.test.net


//Python，使用了 requests，会要求输入client.key的密码 

import requests
requests.get('https://www.test.net', verify=False, cert=('client.crt', 'client.key'))


//使用requests_pkcs12

from requests_pkcs12 import get
r = get('https://www.test.net', pkcs12_filename='client.p12', pkcs12_password='client.key的密码', verify=False)


此外，这个打包文件还可以直接载入浏览器。


参考：

http://blog.nategood.com/client-side-certificate-authentication-in-ngi


