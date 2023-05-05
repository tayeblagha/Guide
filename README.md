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
<h4 style="color: black; font-weight: bold;">Shortcut Here</h4>


 <h6> api (short for api-server) </h6> 
 <h6> cm (short for configmap) </h6>
 <h6> crd (short for custom resource definition) </h6>
 <h6> dep (short for deployment) </h6>
 <h6> etcd (short for distributed key-value store used by Kubernetes) </h6>
 <h6> ns (short for namespace) </h6>
 <h6>pvc (short for persistent volume claim) </h6>
 <h6>svc (short for service) </h6>
<h4 style="color: black; font-weight: bold;">Commands Here</h4>

 

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



