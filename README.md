# SQL queries (with Python) can be found here:

https://github.com/do4am/SQL/blob/master/SQL-queries.ipynb

# Installation SQL server on Ubuntu 

## Host machine runs Window 10:

  * Installation MySQL workbench (optional): https://dev.mysql.com/downloads/installer/
   
  * Installation of Ubuntu server on virtual machine to host SQL server: https://itsfoss.com/install-linux-in-virtualbox/
  
  * Open Oracle VM --> Settings --> Network --> Tab Adapter2 Enable Network Adapter, host-only Adapter

## Virtual Machine runs Ubuntu:

  * Installation of MySQL server: https://support.rackspace.com/how-to/installing-mysql-server-on-ubuntu/

  * Installation sample employees dataset: https://dev.mysql.com/doc/employee/en/employees-installation.html
  
  <p align="center">
    <img width="600" src="employees-schema.png">
  </p>

  * Type ifconfig in terminal to see the ip address of the virtual machine (install neccesary package if asked for)
  
 ## Connect host machine to virtual machine with MySQL workbench: 
 
  * From Ubuntu install nmap: sudo apt install nmap
  
  * I want to bind my SQLserver to different address than the localhost by default, so I command out bind-address 127.0.0.1 (since the server was listening internally only) from /etc/mysql/mysql.conf.d/mysqld.cnf or /etc/mysql/my.cnf (UBUNTU < 16.4)
sudo service mysql restart (default port 3306)

  * test port open or closed for the host address: nmap 192.168.56.101 -p 3306
  
  * if it closed then do the following to grant access to that specific IP address: 
  
  * sudo mysql -u root -p\
    GRANT ALL ON *.* to root@'192.168.56.%' IDENTIFIED BY 'PASSWORLD_UBUNTU';\
    FLUSH PRIVILEGES:\
    sudo ufw allow 3306/tcp\
    sudo service ufw restart\
    sudo service mysql restart\
   
  * check again if it works: nmap 192.168.56.101 -p 3306 and this too: sudo mysql -h 192.168.56.101 -u root -p
  
  * From host machine, open workbench SQL to check the connection:
    Database --> Connect to Database.... \
    Enter IPddr: 192.168.56.101 port: 3306 (by default for SQL server)\
    user root (for me), password\
    set schema: employees (current working databases)
    
 ## Set up python (python 3.6) to work with MySQL:
 
  * In python3.6 env: conda install -c anaconda mysql-connector-python 
  
  * Examples can be found here: https://dev.mysql.com/doc/connector-python/en/connector-python-example-cursor-select.html
  
## Modules:

  * Pandas, mysql-connector-python 
  
