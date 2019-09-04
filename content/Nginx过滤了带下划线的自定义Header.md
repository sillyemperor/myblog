Title: Nginx过滤了带下划线的自定义Header
Date: 2019-06-04
Category: Nginx
Tags: Nginx

服务的需要一个自定义的header，'my_header'，选择'_'而不是'-'的原因就不在这里讨论了。通过nginx反向代理后，传到服务端，'my_header'不见了。问了一下Bing（没用谷歌，也没用Baidu），结果发现nginx里有一个 开关，' underscores_in_headers'，设置为‘off’就会拦截所有带'_'的header，设置为‘on’就放过。缺省是‘off’。所以只要在http或者server中设置一下就好了。


