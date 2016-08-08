# FinbitProject

# This project is intended to do whoever wants to learn with me with the following.
1. Setup your mac as a development machine.
2. Install Homebrew
3. Install Memcached
4. Install ActiveMQ
5. Install Posgres
6. Install Tomcat
7. Install Jenkins
8. Install Ansible
9. Install Docker
10. Install AWS CLI

# How to install Homebrew.

1. This is install xcode and homebrew 

 xcode-select –install

 /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

2. This is install Memcached

 brew install memcached
 
 https://gist.github.com/tomysmile/ba6c0ba4488ea51e6423d492985a7953
 
3. To install ActiveMQ

 Install the App

 Press Command+Space and type Terminal and press enter/return key.
 Run in Terminal app:
 ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" < /dev/null 2> /dev/null
 and press enter/return key. Wait for the command to finish.
 Run:
 brew install activemq

  To have launchd start activemq now and restart at login:
  brew services start activemq
  Or, if you don't want/need a background service you can just run:
  activemq start

4. To install Postgres

  brew install postgres
  initdb /usr/local/var/postgres
  /usr/local/Cellar/postgresql/<version>/bin/createuser -s postgres
  
  To start server at startup

  mkdir -p ~/Library/LaunchAgents
  ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents
  launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
  Now, it is set up, login using psql -U postgres -h localhost or use PgAdmin for GUI.

  By default user postgres will not have any login password.

5. To install Tomcat

   brew install tomcat

   First install with the brew install in terminal:

  $ brew install tomcat
  
  This will take care of the downloading, installation and configuration of not only Tomcat but any dependencies as well.

  Homebrew keeps packages (known as “kegs”) in a “Cellar”, a directory typically located at:

  /usr/local/Cellar/

  To start the Tomcat server, execute the Catalina shell program with the “run” parameter as such:

  $ ls /usr/local/Cellar/tomcat/
  $ /usr/local/Cellar/tomcat/[version]/bin/catalina run
  The version number and installation directory will have been listed by homebrew at the end of the installation output (typically the last line with a beer symbol in front). Catalina can also be set to start on system launch – although for security reasons we prefer to only run when needed (either using this command or more commonly via an IDE plugin).

  Once the server is running you can navigate to the host page at:

  http://localhost:8080/

  To add and manage applications running on the server you will also need to edit a configuration file:

  $ vim /usr/local/Cellar/tomcat/[version]/libexec/conf/tomcat-users.xml
  With [version] again replaced with your installed version. Towards the bottom of this short config file you will see a selection of users – all commented out by default. You need to uncomment one of these and give it the extra role “manager-gui” (preferably also changing the username and password for security). The resultant user entry should look something like this:

  <user username="admin" password="password" roles="tomcat,manager-gui" />
  After this you can navigate to the page (or click the “Manager App” link on the main Tomcat Server page):

  http://localhost:8080/manager/html

  Here you can view or delete the included sample application and deploy your own. Usually it’s easiest to deploy applications in a dev / testing environment using an IDE or other deployment routine, however the web interface is fine also. For reference, deployed applications are usually then located under the directory:

  /usr/local/Cellar/tomcat/[version]/libexec/webapps/

  https://maltronic.io/2016/01/14/easily-install-apache-tomcat-on-mac-os-x-10-11-el-capitan-with-homebrew/
