# database
安装mongodb的step:

1、查看系统版本：   sudo lsb_release -a
2、Import the public key used by the package management system
--sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
3、Create a /etc/apt/sources.list.d/mongodb-enterprise.list file for MongoDB.
according to differnt version：for eaxmple：Ubuntu 16.04


--echo "deb http://repo.mongodb.com/apt/ubuntu xenial/mongodb-enterprise/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-enterprise.list

4、Reload local package database
--sudo apt-get update

5、Install the MongoDB Enterprise packages
--sudo apt-get install -y mongodb-enterprise

6、(Ubuntu 16.04-only) Create systemd service file
Create a new file at /lib/systemd/system/mongod.service with the following contents:

[Unit]
Description=High-performance, schema-free document-oriented database
After=network.target
Documentation=https://docs.mongodb.org/manual

[Service]
User=mongodb
Group=mongodb
ExecStart=/usr/bin/mongod --quiet --config /etc/mongod.conf

[Install]
WantedBy=multi-user.target


<install over>

<start service>
--sudo service mongod start

<stop service>
--sudo service mongod stop

<restart service>
--sudo service mongod restart


<uninstall>
1、Stop MongoDB.
--sudo service mongod stop
2、Remove Packages
--sudo apt-get purge mongodb-enterprise*
3、Remove Data Directories
--sudo rm -r /var/log/mongodb
--sudo rm -r /var/lib/mongodb


安装node.js

1、--sudo apt-get install g++ curl libssl-dev apache2-utils git-core build-essential
2、--git clone git://github.com/ry/node.git
3、--cd node
4、--./configure
5、--make
6、--sudo make instal
