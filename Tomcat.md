# Apache Tomcat

## Table of Content

* [APACHE TOMCAT](#1.APACHE-TOMCAT)
* [Install JDK](#Install-JDK)	  
  Step 1 — Installing JDK   
  Step 2 – Check java version  
* [Install Tomcat 9](#Install-Tomcat-9)	  
  Step 1 — Creating a Tomcat user and group	  
  Step 2 — Download and Install Tomcat 9	    
  Step 3 — Change Permission and Ownership of the Tomcat home directory	  
  Step 4 — Creating a SystemID Service File for Tomcat	  
  Step 5 — Enable and Secure Tomcat Web Application and Virtual Host Manager	  
  Step 6 — Configure Tomcat Web Application Manager	  
  Step 7 — Configure Tomcat Virtual Host Manager	




**Environment Info**  
Server Info-  
Os version  
NAME="Ubuntu"  
VERSION="20.04.6 LTS (Focal Fossa)"  


### List of Tools:- 

1.Apache Tomcat  
2.Install JDK  
3.Install Tomcat 9

#### 1.APACHE TOMCAT

Apache Tomcat is an open-source implementation of the Java Servlet, JavaServer Pages (JSP), and Java Expression Language technologies. It is developed by the Apache Software Foundation and provides a lightweight, efficient environment for running Java-based web applications.

#### 2.Install JDK

 Tomcat 9 requires Java 8 or later versions to work. You can check and verify that Java is   installed with the following command.

**Step 1 — Installing JDK**
~~~
sudo apt install default-jdk
~~~

**Output-**
``````  
tusha@tusha:~$ sudo apt install default-jdk
[sudo] password for tusha:
Reading package lists... Done
Building dependency tree  	 
Reading state information... Done
The following additional packages will be installed:
  default-jdk-headless default-jre default-jre-headless libice-dev libpthread-stubs0-dev libsm-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev
  libxt-dev openjdk-11-jdk openjdk-11-jdk-headless x11proto-core-dev x11proto-dev xorg-sgml-doctools xtrans-dev
Suggested packages:
  libice-doc libsm-doc libx11-doc libxcb-doc libxt-doc openjdk-11-demo openjdk-11-source visualvm
The following NEW packages will be installed:
  default-jdk default-jdk-headless default-jre default-jre-headless libice-dev libpthread-stubs0-dev libsm-dev libx11-dev libxau-dev libxcb1-dev
  libxdmcp-dev libxt-dev openjdk-11-jdk openjdk-11-jdk-headless x11proto-core-dev x11proto-dev xorg-sgml-doctools xtrans-dev
0 upgraded, 18 newly installed, 0 to remove and 7 not upgraded.
Need to get 76.9 MB of archives.
After this operation, 90.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://in.archive.ubuntu.com/ubuntu focal/main amd64 default-jre-headless amd64 2:1.11-72 [3,192 B]
Get:2 http://in.archive.ubuntu.com/ubuntu focal/main amd64 default-jre amd64 2:1.11-72 [1,084 B]
Get:3 http://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 openjdk-11-jdk-headless amd64 11.0.21+9-0ubuntu1~20.04 [73.7 MB]
Get:4 http://in.archive.ubuntu.com/ubuntu focal/main amd64 default-jdk-headless amd64 2:1.11-72 [1,140 B]                                       	 
Get:5 http://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 openjdk-11-jdk amd64 11.0.21+9-0ubuntu1~20.04 [1,332 kB]                     	 
Selecting previously unselected package default-jdk.
Setting up default-jdk (2:1.11-72) ...
Setting up libxdmcp-dev:amd64 (1:1.1.3-0ubuntu1) ...
Setting up x11proto-core-dev (2019.2-1ubuntu1) ...
Setting up libxcb1-dev:amd64 (1.14-2) ...
Setting up libx11-dev:amd64 (2:1.6.9-2ubuntu1.6) ...
Setting up libxt-dev:amd64 (1:1.1.5-1) ...
Processing triggers for man-db (2.9.1-1) ...

``````

After installation check, if java is installed correctly by executing below command.

**Step 2 – Check java version**  
``````
java  -version
``````
**Output-**

``````  
tusha@tusha:~$ java -version
openjdk version "11.0.21" 2023-10-17
OpenJDK Runtime Environment (build 11.0.21+9-post-Ubuntu-0ubuntu120.04)
OpenJDK 64-Bit Server VM (build 11.0.21+9-post-Ubuntu-0ubuntu120.04, mixed mode, sharing)
``````

#### 3.Install Tomcat 9  
**Step 1 — Creating a Tomcat user and group**  

We should not run tomcat under the root user for security reasons. Let’s create a group tomcat and add a user tomcat to it. Additionally, we are going to install tomcat under /opt/tomcat directory which will be tomcat user home directory:
``````
sudo groupadd tomcat
````
````
sudo useradd -s /bin/false  -d /opt/tomcat tomcat
``````
**Output-**  
```
tusha@tusha:~$ sudo groupadd tomcat
[sudo] password for tusha:
groupadd: group 'tomcat' already exists
tusha@tusha:~$ sudo useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat
useradd: user 'tomcat' already exists
tusha@tusha:~$
``````

**Step 2 — Download and Install Tomcat 9**  

Download and Install Tomcat 9.0.21 archive file using the following commands. You can also visit the official download page to download the latest available version.
We are going to install Tomcat to the **/opt** directory. So we will download the Tomcat 9.0.21 package to that location.
Change directory to /opt and download Tomcat 9 to that directory.  

``````
cd /opt
sudo wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.21/bin/apache-tomcat-9.0.21.tar.gz
``````
**Output-**
``````
tusha@tusha:~$  cd /opt
tusha@tusha:/opt$ sudo wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.21/bin/apache-tomcat-9.0.21.tar.gz
--2023-12-18 10:44:38--  https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.21/bin/apache-tomcat-9.0.21.tar.gz
Resolving archive.apache.org (archive.apache.org)... 65.108.204.189, 2a01:4f9:1a:a084::2
Connecting to archive.apache.org (archive.apache.org)|65.108.204.189|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10874669 (10M) [application/x-gzip]
Saving to: ‘apache-tomcat-9.0.21.tar.gz’
apache-tomcat-9.0.21.tar.gz       	100%[=======================================================================>]  10.37M   521KB/s	in 16s	 
2023-12-18 10:44:56 (656 KB/s) - ‘apache-tomcat-9.0.21.tar.gz’ saved [10874669/10874669]
tusha@tusha:/opt$
``````

**A.** Extract the tar package and rename the extracted directory to tomcat
```
sudo tar -xvzf apache-tomcat-9.0.21.tar.gz
sudo mv apache-tomcat-9.0.21/* /opt/tomcat/
``````
**Output-**
``````   
tusha@tusha:/opt$ sudo tar -xvzf apache-tomcat-9.0.21.tar.gz
apache-tomcat-9.0.21/conf/
apache-tomcat-9.0.21/conf/catalina.policy
apache-tomcat-9.0.21/conf/catalina.properties
apache-tomcat-9.0.21/conf/context.xml
apache-tomcat-9.0.21/conf/jaspic-providers.xml
apache-tomcat-9.0.21/conf/jaspic-providers.xsd
apache-tomcat-9.0.21/conf/logging.properties
apache-tomcat-9.0.21/conf/server.xml
apache-tomcat-9.0.21/webapps/docs/appdev/sample/web/
apache-tomcat-9.0.21/webapps/docs/appdev/sample/web/WEB-INF/
apache-tomcat-9.0.21/webapps/docs/appdev/sample/web/images/
apache-tomcat-9.0.21/webapps/docs/architecture/
apache-tomcat-9.0.21/webapps/docs/architecture/requestProcess/
apache-tomcat-9.0.21/webapps/docs/architecture/startup/
apache-tomcat-9.0.21/bin/catalina.sh
apache-tomcat-9.0.21/bin/ciphers.sh
apache-tomcat-9.0.21/bin/configtest.sh
apache-tomcat-9.0.21/bin/daemon.sh
apache-tomcat-9.0.21/bin/digest.sh
apache-tomcat-9.0.21/bin/makebase.sh
apache-tomcat-9.0.21/bin/setclasspath.sh
apache-tomcat-9.0.21/bin/shutdown.sh
apache-tomcat-9.0.21/bin/startup.sh
apache-tomcat-9.0.21/bin/tool-wrapper.sh
apache-tomcat-9.0.21/bin/version.sh
tusha@tusha:/opt$ sudo mv apache-tomcat-9.0.21 /opt/tomcat
tusha@tusha:/opt$
``````

**Step 3 — Change Permission and Ownership of the Tomcat home directory**

Next, we will modify ownership and permission of the /opt/tomcat directory. We will also give executed permission to opt/tomcat/bin/ directory.

```
sudo chown -R tomcat: /opt/tomcat/bin/
``````
**Output-**  
``````
tusha@tusha:/opt$ sudo chown -R tomcat: /opt/tomcat
``````

**Step 4 — Creating a SystemID Service File for Tomcat**  

**A.** To install Tomcat as system service we will create a file called tomcat.service in the **/etc/systemd/system** directory.  
``````
sudo vim /etc/systemd/system/tomcat.service
``````
**B.** Add the following to tomcat.service file
``````
[Unit]
Description=Tomcat 9 Server
After=network.target
[Service]
Type=forking
User=tomcat
Group=tomcat
Environment="JAVA_HOME=/usr/lib/jvm/default-java"
# java 17 path /usr/lib/jvm/java-1.11.0-openjdk-amd64
Environment="JAVA_OPTS=-Xms512m -Xmx512m"
Environment="CATALINA_BASE=/opt/tomcat"
Environment="CATALINA_HOME=/opt/tomcat"
Environment="CATALINA_PID=/opt/tomcat/temp/tomcat.pid"
Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"
ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh
# use when you want to run as root ExecStart=/bin/sh -c '/opt/tomcat/bin/startup.sh'
# use when you want to run as root ExecStop=/bin/sh -c '/opt/tomcat/bin/shutdown.sh'
UMask=0007
RestartSec=10
Restart=always
[Install]
WantedBy=multi-user.target
``````

**C.** Save and exit.

**D.** Restart systemctl daemon.
``````
sudo systemctl daemon-reload  
``````
**E.** To start the tomcat service.
``````
sudo systemctl start tomcat
``````
**F.** To monitor the Tomcat log file.
``````
sudo tail -f /opt/tomcat/logs/catalina.out
``````
**Output-**  
``````
tusha@tusha:/opt$ sudo tail -f /opt/tomcat/logs/catalina.out
27-Dec-2023 14:52:49.699 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/opt/tomcat/webapps/host-manager] has finished in [49] ms
27-Dec-2023 14:52:49.699 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/opt/tomcat/webapps/examples]
27-Dec-2023 14:52:49.994 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/opt/tomcat/webapps/examples] has finished in [295] ms
27-Dec-2023 14:52:49.994 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/opt/tomcat/webapps/ROOT]
27-Dec-2023 14:52:50.010 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/opt/tomcat/webapps/ROOT] has finished in [16] ms
27-Dec-2023 14:52:50.011 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/opt/tomcat/webapps/manager]
27-Dec-2023 14:52:50.033 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/opt/tomcat/webapps/manager] has finished in [22] ms
27-Dec-2023 14:52:50.037 INFO [main] org.apache.coyote.AbstractProtocol.start Starting ProtocolHandler ["http-nio-8080"]
27-Dec-2023 14:52:50.053 INFO [main] org.apache.coyote.AbstractProtocol.start Starting ProtocolHandler ["ajp-nio-8009"]
27-Dec-2023 14:52:50.089 INFO [main] org.apache.catalina.startup.Catalina.start Server startup in [798] milliseconds
``````
**G.** Access Deployed  

```
http://localhost:8080/
``````
![](https://lh7-us.googleusercontent.com/QnY_u5WHHLjFXiZdbWc7zvTfrv-08eMXmRqmO9MF0CAhx7O2awsdCJmwURb_sVmS3KBUFTQN88ZEBj0JcedAzymM9DbONbAt3W5boZL3OzzZ8PVV4QAYhbv5WaGbNG_tqQU-YYxcyj04Ccs2ehtojtE)

**H.** To enable Tomcat service on system boot:
``````
sudo systemctl enable tomcat
``````
**Output-**
``````
Created symlink /etc/systemd/system/multi-user.target.wants/tomcat.service → /etc/systemd/system/tomcat.service.
``````

**I.** The default Tomcat port is 8080, so we need to allow that port on the Ubuntu firewall.
``````
sudo ufw allow 8080/tcp
``````
**Output-**  
``````
 tusha@tusha:/opt$ sudo ufw allow 8080/tcp
Rules updated
Rules updated (v6)
``````
**J.** Check firewall status 
`````` 
sudo ufw status
``````

**Output-**  
``````
tusha@tusha:/opt$ sudo ufw status
Status: inactive
``````

**K.** Enable ufw
``````
sudo systemctl enable ufw
``````
**Output-**  
``````
tusha@tusha:/opt$ sudo systemctl enable ufw
Synchronizing state of ufw.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable ufw
sudo systemctl start ufw
Output-
tusha@tusha:/opt$ sudo systemctl status ufw
● ufw.service - Uncomplicated firewall
 	Loaded: loaded (/lib/systemd/system/ufw.service; enabled; vendor preset: enabled)
 	Active: inactive (dead) since Wed 2023-12-27 16:33:20 IST; 10s ago
   	Docs: man:ufw(8)
	Process: 23675 ExecStop=/lib/ufw/ufw-init stop (code=exited, status=0/SUCCESS)
   Main PID: 302 (code=exited, status=0/SUCCESS)
Dec 27 16:33:20 tusha systemd[1]: Stopping Uncomplicated firewall...
Dec 27 16:33:20 tusha ufw-init[23675]: Skip stopping firewall: ufw (not enabled)
Dec 27 16:33:20 tusha systemd[1]: ufw.service: Succeeded.
Dec 27 16:33:20 tusha systemd[1]: Stopped Uncomplicated firewall.
Warning: journal has been rotated since unit was started, output may be incomplete.
``````

**Step 5 — Enable and Secure Tomcat Web Application and Virtual Host Manager**  

Tomcat has a Web Application Manager and Virtual Host Manager app that come preinstalled. In order to use these, we have to first secure them with authentication and authorization. This is done via the tomcat-users.xml file. Open and edit tomcat-users.xml:
``````
sudo vim /opt/tomcat/conf/tomcat-users.xml
``````
Add the following between tags and save. The roles required to access Web Application Manager and Virtual Host Manager are manager-gui and admin-gui respectively.

In this case you have to change your username and password according to you.

``````
<role rolename="admin-gui"/><role rolename="manager-gui"/><user username="tusha" password="12345" roles="admin-gui,manager-gui"/>
``````
![](https://lh7-us.googleusercontent.com/uAUL9KbCvwyZCaTG3pOrSTbrcmkBYEAbrmMgmL5nmOEIUfgY2-bacaxGqhzKS9Wv6DGMuFrkznQfSOC5i1-YRG3hkRHR1hYhVHQbgYjQ8cwlvh4NRhTYp-ClPHL8jcyg06EVLy_LnHHG16h2ISnCIQs)


**Step 6 — Configure Tomcat Web Application Manager**

The Tomcat web application manager is configured to allow access only from the localhost. To allow remote access we have to edit the /opt/tomcat/webapps/manager/META-INF/context.xml  
This is not recommended for production environments.

**A.** Open the context.xml file

``````
sudo vim /opt/tomcat/webapps/manager/META-INF/context.xml
``````
**B.** Comment the lines as shown below
``````
<Valve className="org.apache.catalina.valves.RemoteAddrValve" allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
``````
![](https://lh7-us.googleusercontent.com/h1XXx-yAemW_uZV5R8gLs0j9_wQIYY4pQBuVOeRAfhJ9NvxYPgS8X8SmLtwnBd52NMvHvsICLJIV6B8d2JZrXvwDNsdhXp1qVpJerb5cZt2WCZeexzIVdK-byN5odt6GZcUZ6ZmlVufroFpjdELVfJY)


**C.** Save and exit.


**D.** Restart tomcat service for changes to take effect.
``````
sudo systemctl restart tomcat
``````
**E.** After Tomcat is restarted we can access the Web Application Manager console at the following link.
``````
http://localhost:8080/manager/html
``````
![](https://lh7-us.googleusercontent.com/kufy0Y_FTin6sXacTMe-R7io7CsDi6qRj6tbci2OPAsYSMttUkIYV_Kq0cTZ-zITXq1phX0s9Yxkud1mc71wtTznOQ587yXsLA8KYmOrfkhr3DY8IhHKvGr3EhKiqL6DWQ1oxr6XO9bc_FUmwJOpS2I)

**F.** Enter the user and password as configured in Step 5. 


**Step 7 — Configure Tomcat Virtual Host Manager**

The Tomcat virtual host manager is configured to allow access only from the localhost. To allow remote access we have to edit the
``````
/opt/tomcat/webapps/host-manager/META-INF/context.xml
``````
This is not recommended for production environments.

**A.** Open the context.xml file
``````
sudo vim /opt/tomcat/webapps/host-manager/
META-INF/context.xml
``````
Comment the lines as shown below:
``````
<Valve className="org.apache.catalina.valves.RemoteAddrValve"allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />      
``````
![](https://lh7-us.googleusercontent.com/nv_7yi0nTpEpwB1C6EeQ7TdET0ZL9UTX5HOdTaUAjJiLmDrpoetGZlbbRkIh1BAQAaByGL_d0ymDpNz2_0Q66V0R4vVxhSGbiXWxsdaxM44Y69iNsqP2Yxysrva3DeMG6m23LYAN_rB-7EP7hjZ69vM)


**B.** Save and exit.  
 **:wq!**  

**C.** Restart tomcat service for changes to take effect.
``````
sudo systemctl restart tomcat
``````
After Tomcat is restarted we can access the Virtual Host Manager console at the following link.
``````
http://localhost:8080/host-manager/html
``````

![](https://lh7-us.googleusercontent.com/9IcaTgKm8KmS9UZ_NZykpEYIcloCv_Oyb5p5qm3Fx520y1GXtaCLgsO6kM7wyr3Pu12NoCecVuswKx8Qr2hYZGwEGIQqnCBxGREISNUJ_PMpaBpAm4PD6WoIzhjiS8A7ELsJxMNWuJ13KGN05Pqbj7k)














