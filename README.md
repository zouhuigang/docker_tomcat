当前版本 Tomcat 7.0.55
运行需求

256M内存及以上
说明

容器启动后会自动创建一个具有所有权限的admin用户，并自动生成随机密码。你可以通过查看容器log获得密码，比如

    => Creating and admin user with a random password in Tomcat

    => Done!

    ========================================================================

    You can now configure to this Tomcat server using:

    admin:1Bwjynh6rAb5

    ========================================================================

在上面的例子中，1Bwjynh6rAb5 就是admin用户的密码。

你可以用admin用户访问下面的地址配置Tomcat:

－ http://your-tomcat-url/manager/html

－ http://your-tomcat-url/host-manager/html

如果你想为admin用户设置一个特定的密码，你可以设置环境变量 TOMCAT_PASS 为您需要的密码。



Usage

To create the image tutum/tomcat, execute the following command on the tutum-docker-tomcat folder:

docker build -t tutum/tomcat .

To run the image and bind to port :

docker run -d -p 8080:8080 tutum/tomcat

The first time that you run your container, a new user admin with all privileges
will be created in Tomcat with a random password. To get the password, check the logs
of the container by running:

docker logs <CONTAINER_ID>

You will see an output like the following:

========================================================================
You can now connect to this Tomcat server using:

    admin:b1uKcRK3r6SF

Please remember to change the above password as soon as possible!
========================================================================

In this case, b1uKcRK3r6SF is the password allocated to the admin user.

You can now login to you admin console to configure your tomcat server:

http://127.0.0.1:8080/manager/html
http://127.0.0.1:8080/host-manager/html

Setting a specific password for the admin account

If you want to use a preset password instead of a random generated one, you can
set the environment variable TOMCAT_PASS to your specific password when running the container:

docker run -d -p 8080:8080 -e TOMCAT_PASS="mypass" tutum/tomcat

You can now test your deployment:

http://127.0.0.1:8080/

Done!