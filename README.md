# Tomcat-setup
This repository will show how to setup the tomcat successfully. 

Tomcat Installation Guide
This guide provides instructions for installing Apache Tomcat 9.0.65 on a Linux system.

Installation Steps
Acquire Root Privileges:

bash
sudo su
Navigate to the /opt Directory:

bash
cd /opt
Download Tomcat:

bash
sudo wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.65/bin/apache-tomcat-9.0.65.tar.gz
Extract the Archive:

bash
sudo tar -xvf apache-tomcat-9.0.65.tar.gz
Configure User Roles:

Edit the tomcat-users.xml file:

bash
cd /opt/apache-tomcat-9.0.65/conf
sudo vi tomcat-users.xml
Add the following line just before the closing </tomcat-users> tag:

xml
<user username="admin" password="admin1234" roles="admin-gui, manager-gui, manager-script"/>
Create Symbolic Links for Startup/Shutdown Scripts:

bash
sudo ln -s /opt/apache-tomcat-9.0.65/bin/startup.sh /usr/bin/startTomcat
sudo ln -s /opt/apache-tomcat-9.0.65/bin/shutdown.sh /usr/bin/stopTomcat
Configure Remote Access (Manager App):

Edit /opt/apache-tomcat-9.0.65/webapps/manager/META-INF/context.xml:

bash
sudo vi /opt/apache-tomcat-9.0.65/webapps/manager/META-INF/context.xml
Comment out the RemoteAddrValve to allow access from any address:

xml
<!-- <Valve className="org.apache.catalina.valves.RemoteAddrValve"
allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->
Configure Remote Access (Host Manager App):

Edit /opt/apache-tomcat-9.0.65/webapps/host-manager/META-INF/context.xml:

bash
sudo vi /opt/apache-tomcat-9.0.65/webapps/host-manager/META-INF/context.xml
Comment out the RemoteAddrValve to allow access from any address:

xml
<!-- <Valve className="org.apache.catalina.valves.RemoteAddrValve"
allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->
Start/Stop Tomcat:

bash
sudo stopTomcat
sudo startTomcat
This guide provides a comprehensive installation process for Apache Tomcat 9.0.65, including configuration for remote access to the manager and host manager applications.
