Title: 几种Python Web Framework性能比较
Date: 2019-06-04
Category: Python
Tags: Python,tornado,flask,falcon,bottle,djiango,ab

参与比较的Python框架有：tornado,flask,falcon,bottle,djiango

测试采用ab命令。

操作系统是：CentOS  7.2 64位。

硬件指标：CPU： 4核    内存：8 GB。

测试时使用2核。

容器采用uwsgi和gunicorn

Python采用CPython2.7和pypy5.0。

测试代码下相应GET请求返回文字“Hello World”，没有模板，没有数据库请求等额外开销。

测试结果：

测试脚本“ab -n 1000 -c 100 http://192.168.0.102:9090/”
![1000](/images/ab-n1000.png)
测试脚本“ab -n 10000 -c 100 http://192.168.0.102:9090/”
![1000](/images/ab-n10000.png)
其中没有结果的是测试数据没有完成就断开连接了。

结论：性能最好的组合是falcon+gunicorn+pypy。该组合适合用于实现微服务。django虽然在性能上不是最优但是作为功能最完整的框架依然适合中大型应用的开发。tornado还没有在实际应用中使用过，有了解的朋友请补充一下。
