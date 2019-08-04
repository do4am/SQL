# SQL query can be found here:



# Installation SQL server on Ubuntu 

## Host machine runs Window 10:

  * Installation MQSQL workbench (optional): https://dev.mysql.com/downloads/installer/
   
  * Installation of Ubuntu server on virtual machine to host SQL server: https://itsfoss.com/install-linux-in-virtualbox/
  
  * Open Oracle VM --> Settings --> Network --> Tab Adapter2 Enable Network Adapter, host-only Adapter

## Virtual Machine runs Ubuntu:

  * Installation of MySQL server: https://support.rackspace.com/how-to/installing-mysql-server-on-ubuntu/

  * Installation sample employees dataset: https://dev.mysql.com/doc/employee/en/employees-installation.html
  
  <p align="center">
    <img width="600" src="employees-schema.png">
  </p>

  
 ## Connect host machine to virtual machine with MySQL workbench:
 
  * From Ubuntu install nmap: sudo apt install nmap
  
  * Command out bind-address 127.0.0.1 (since the server was listening internally only) from /etc/mysql/mysql.conf.d/mysqld.cnf or /etc/mysql/my.cnf (UBUNTU < 16.4)
sudo service mysql restart (default port 3306)

  * test port open or closed for the host address: nmap 192.168.56.101 -p 3306
  
