# Jenkins

*** Prerequisites

- master - 192.168.1.6
- slave - 10.0.2.15


*** Step 1 - Jenkins Master Node

$ java
$ sudo apt install openjdk-11-jre-headless or sudo apt install default-jre
$ java -version
$ wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
$ sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
$ sudo apt update
$ sudo apt install jenkins
$ sudo systemctl status jenkins
$ sudo systemctl status jenkins
$ sudo ufw allow 8080
$ sudo ufw allow OpenSSH
$ sudo ufw allow proto tcp from 192.168.121.0/24 to any port 8080
$ sudo ufw enable
$ sudo ufw status
$ sudo su - jenkins
$ whoami
$ ssh-keygen
enter
enter
enter

[$ cd .ssh/
$ cat id_rsa.pub
copy the key]


*** Step 2 - Jenkins Slave Node

$ sudo apt update
$ sudo apt install openjdk-11-jre-headless or sudo apt install default-jre
$ useradd jenkins -md /home/jenkins -s /bin/bash    or   $ sudu adduser jenkins
enter
enter
enter
enter
enter
y
$ sudo su - jenkins
$ whoami

[$ mkdir ~/.ssh
$ touch ~/.ssh/authorized_keys
$ vim ~/.ssh/authorized_keys
paste
:wq]
$ sudo ufw allow 8080
$ sudo ufw allow OpenSSH
$ sudo ufw allow proto tcp from 192.168.121.0/24 to any port 8080
$ sudo ufw enable
$ sudo ufw status
$ ip r / $ ip address / $ ifconfig / $ hostname -I
copy ip


*** Step 3 - Jenkins Master Node


$ ssh-copy-id jenkins@10.0.2.15 (paste ip)
yes
$ sudo usermod -L
$ ssh jenkins@10.0.2.15
Exit
[Here we are able to access the jenkins slave without password ]


*** Step 4 - Adding Slave Nodes

- Go to browser seaarch bar > localhost:8080 > Manage Node > New Node > node name (slave01) >  permanent agent > OK > remote root directory (/home/jenkins) > Launch method (via SSH) > Host (slave ip address/DNS) > credentials > add (jenkins) > kind (ssh username with private key) > username (jenkins1) > private key (enter directly) > go to master node terminal > $ cd .ssh/ > cat id_rsa > copy key > back to jenkins dashboard > paste > add > credentials (jenkins1) > host key verification strategy (known hosts file verification strategy/ trusted key ) > save > lanch agent > agent successfully connected > go to master node terminal > $ sudo ls /home/parvez/ > check slave.jar


*** Step 5 - Testing

- back to jenkins dashboard > create a job > slave > job > pipeline > ok > pipeline (Hello world) > save > build now > console output > successfull

