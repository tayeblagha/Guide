# Guide
![](http://i.imgur.com/y8g506n.png?1)



A `guide ` and some usefull `commands` in devops.

## Docker  <a href="https://www.docker.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg" alt="docker" width="30" height="30"/> </a>
```bash
docker run -d -p 3307:3306 --name mysqldbv1 -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=test mysql
docker network create spring-net
docker network ls
docker network connect spring-net mysqldbv1
docker container inspect mysqldbv1
docker run -d -p 3307:3306 --name mysqldbv2 --network=spring-net -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=test mysql
docker exec -it mysqldbv1 /bin/sh
```
## Kubernetes  <a href="https://kubernetes.io" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/kubernetes/kubernetes-icon.svg" alt="kubernetes" width="30" height="30"/> </a> 
#### <span style="color:black;font-weight:bold;">Shortcut</span>


 <h6> api (short for api-server) </h6> 
 <h6> cm (short for configmap) </h6>
 <h6> crd (short for custom resource definition) </h6>
 <h6> dep (short for deployment) </h6>
 <h6> etcd (short for distributed key-value store used by Kubernetes) </h6>
 <h6> ns (short for namespace) </h6>
 <h6>pvc (short for persistent volume claim) </h6>
 <h6>svc (short for service) </h6>
 <span style="color:black;font-weight:bold;">Commands</span>

 

```bash
kubectl delete all --all -n default
kubectl get po [pod_name] -o jsonpath='{.metadata.uid}'
kubectl exec -it secret-vol-pod -- /bin/sh
kubectl api-resources
kubectl expose deployment twipbox --type=LoadBalancer --name=twipbox-service --port=80 --target-port=8080
kubectl expose deployment twipbox --type=NodePort --name=twipbox-service --port=80 --target-port=8080
kubectl port-forward service/mywebapp 8080:80
kubectl get pod -l app:myapp
kubectl logs -l app=web,env=prod -c my-container   (-f to persist viewing)
kubectl rollout restart deployment dep
kubectl create secret docker-registry regcredential --docker-server=docker.io --docker-username=[docker_username] --docker-password=[docker-password] --docker-email=[docker-email]
kubectl get secret regcredential --output=yaml
```

### Forticlient Vpn <a href="#" target="_blank" rel="noreferrer"> <img src="https://images.sftcdn.net/images/t_app-icon-s/p/87f45a9e-96d4-11e6-b8fa-00163ec9f5fa/1944140565/fortinet-icon.png" alt="kubernetes" width="30" height="30"/> </a> :

connect to forticlient vpn using only commands** 

Open your terminal and type the following command to download the Fortigate SSLVPN CLI:   
```bash
wget http://cdn.software-mirrors.com/forticlientsslvpn_linux_4.4.2328.tar.gz
```

Once the download is complete, you need to uncompress the downloaded file by running the following command:
```bash
tar -xzvf forticlientsslvpn_linux_4.4.2328.tar.gz
```

If you don't already have ppp installed, you can install it by running the following command:
```bash
		sudo apt-get install ppp
```
Go to the installer setup directory by running the following command:
```bash
		cd ./forticlientsslvpn/64bit/helper
```
Run the setup file with the following command:
```bash
		sudo ./setup.linux.sh
```
Once the setup is complete, go to the following directory:
```bash
		cd ../..
		cd forticlientsslvpn/64bit/
```
Finally, you can connect to the VPN server whenever you want by running the following command:
```bash
		./forticlientsslvpn_cli --server [Server_Address:Port] --vpnuser admin
```
You will be prompted to enter your password, which is "***********************".

## Spring Boot Service   <a href="#" target="_blank" rel="noreferrer"> <img src="https://png.pngtree.com/png-clipart/20200224/original/pngtree-light-bulb-logo-new-idea-symbol-and-icon-flat-bright-cartoon-png-image_5212484.jpg" alt="service" width="30" height="30"/> </a> 
Make sure to edit you pom.xml and add configuration/executable to it like this and create your jar by running mvn package :
```bash
		<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
				<configuration>
					<executable> true</executable>
				</configuration>
			</plugin>
		</plugins>
		<finalName>spring-boot-service</finalName>

	</build>
```

#### <span style="color:black;font-weight:bold;">Make a Service from Jar in Linux <img src="https://1000logos.net/wp-content/uploads/2017/03/LINUX-LOGO-453x500.png" alt="service" width="30" height="30"/> </a>  </span>
create service called app1.service
```bash
sudo nano /etc/systemd/system/app1.service
```
Add the fellowing:
```bash
[Unit]
Description=Spring init sample
After=syslog.target

[Service]
User=tayeb
Restart=always
RestartSec=30s
ExecStart=/usr/bin/java -jar /home/tayeb/Documents/serviceTraining/spring-boot-service.jar
SuccessExitStatus=143

[Install]
WantedBy=multi-user.target
```
Simply start it with this command 
```bash
sudo systemctl start app1.service
```
To make it run automatically you can once restart use:
```bash
sudo systemctl enable app1.service
```
#### <span style="color:black;font-weight:bold;">Make a Service from Jar in Windows  <img src="https://www.downloadsource.net/image/uploaded/English_2021_Q1/Windows_11_Boot_Screen_Animation/Windows_11_hidden_boot_menu_animation_enable.jpg?fm=webp&s=22b011c445329f4c33434fb37a70696d" alt="service" width="30" height="30"/> </a>  </span>
<h5> Download  sample-minimal.xml  and  WinSW.NET4.exe from the fellowing github link <a  target="_blank" href="https://github.com/winsw/winsw/releases"> click here </a> </h5>
<h5> Create a folder containg the two downloaded folders and your jar file. </h5>
<img src="https://github.com/tayeblagha/Guide/blob/main/windowsservice.png?raw=true" alt="service" width="450" height="150"/>
<h5> open cmd as administrator  and then go to your folder location and edit sample-minimal.xml as the fellowing : </h5>

```xml
<service>
  <!-- ID of the service. It should be unique across the Windows system-->
  <id>servicename</id>
  <!-- Display name of the service -->
  <name>servicename</name>
  <!-- Service description -->
  <description>This service is a service created from a minimal configuration</description>
  
  <!-- Path to the executable, which should be started -->
  <executable>java</executable>
    <arguments>  -Xmx1548m -Xms800m -jar jarName.jar</arguments>
</service>
```

save and exit and than rename your  sample-minimal.xml to WinSW.NET4.xml and run this cmd as administrator  :  
```bash
WinSW.NET4.exe install
```
## Mega tools Backup  <a href="https://kubernetes.io" target="_blank" rel="noreferrer"> <img src="https://img.freepik.com/free-vector/cloud-network-technology-icon-blue-gradient-background_53876-119510.jpg?t=st=1683303874~exp=1683304474~hmac=0f8343f16d181fe9a40a3d55f36aed92758994eb53cc4a0383582573f576296a" alt="kubernetes" width="30" height="30"/> </a> 
you need first to intall megaZ tools as the fellowing:
```bash
sudo apt-get install libssl1.1
wget https://mega.nz/linux/MEGAsync/xUbuntu_20.04/amd64/megacmd-xUbuntu_20.04_amd64.deb
sudo apt install ./megacmd*.deb
```
create Folder called script and than create file in it like the fellowing:
```bash
mkdir -p ~/scripts/db_backup.sh
sudo chmod +x ~/scripts/db_backup.sh
nano ~/scripts/db_backup.sh
```
add the fellowing script: 
```xml
#!/bin/bash

# Set the MySQL credentials
USER="factar"
PASSWORD="factardb@2022"

# Set the backup directory
BACKUP_DIR="/home/user/db_backups"

# Set the MEGA directory for backups
MEGA_DIR="/Backups/MySQL"

# Create a new directory for today's backup
NOW=$(date +"%d-%m-%Y_%H-%M")
BACKUP_PATH="$BACKUP_DIR/$NOW"
mkdir -p "$BACKUP_PATH"

# Dump the MySQL database to a file in the backup directory
MYSQL_PWD="$PASSWORD" mysqldump -u "$USER" factar > "$BACKUP_PATH/factar.sql"

# Upload the backup file to MEGA using mega-put
mega-put "$BACKUP_PATH/factar.sql"   "$TODAY/factar.sql"
```
login to you mega account using this command:
```bash
mega-login [emai] [password]
```
now you run this script successfully with 
```bash
cd ~/scripts
./db_backup.sh
```
To automate Sending Backup everyDay we can use cron job:
```bash
crontab -e
```
For example this cron job will run the db_backup.sh script located in the ~/scripts/ directory every day at 1:00 AM.
```xml 
# Edit this file to introduce tasks to be run by cron.
0 1 * * * ~/scripts/db_backup.sh
# Each task to run has to be defined through a single line
```

### Gitalb CI/CD   <img src="https://secrethub.io/img/gitlab-ci.png" alt="docker" width="30" height="30"/> 
AWS S3 (simple storage service)    <img src="https://w7.pngwing.com/pngs/564/59/png-transparent-amazon-com-amazon-s3-amazon-web-services-amazon-simple-queue-service-amazon-glacier-bucket-miscellaneous-data-amazon-dynamodb.png" width="30" height="30"/>
<h6> Create S3 bucket from aws  </h6>
<img src="https://github.com/tayeblagha/Guide/blob/main/1.png?raw=true"  length="900" height="280"/>


