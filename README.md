# docker-tomcat
基于Centos7.2+JDK1.8制作的Tomcat镜像

支持的标签，以及对应的 Dockerfile
8.5 (8.5/jre8/Dockerfile)

快速参考
维护者: ganbing87@126.com

本镜像的特点
已设置时区为：Asia/Shanghai。
解决了某些云服务器上Tomcat启动过慢问题（随机数产生器初始化过慢）。

如何使用本镜像

1、测试启动Tomcat:
$ docker run -it --rm -p 8888:8080 ganbing87/docker-tomcat:latest
可以通过浏览器访问 http://localhost:8888 或 http://host-ip:8888 来测试Tomcat是否启动成功。

2、部署应用，启动Tomcat:
例如：将/home/myapp，部署成根路径项目，并将Tomcat和myapp的日志，均输出到/home/myappLogs目录。

$ docker run -d --name tomcat-myapp -p 8888:8080 \ 
	-v /home/myapp:/usr/local/tomcat/webapps/ROOT \ 
	-v /home/myappLogs:/usr/local/tomcat/logs \ 
	dfengwei/docker-tomcat:latest
  
注意：myapp的日志文件输出路径须为相对路径：logs（对应的绝对路径为：{$CATALINA_HOME}/logs）。
Tomcat环境相关:
CATALINA_HOME:   /usr/local/tomcat
JRE_HOME:        /usr
