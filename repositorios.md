
### 1.- Añadir repositorios.

``` ruby 
helm repo add "stable" "https://charts.helm.sh/stable" --force-update
helm repo add bitnami https://charts.bitnami.com/bitnami --force-update
```

![k0s](https://github.com/anasalasro/Kubernetes-Helm/blob/main/imagenes/a%C3%B1adirRepo.png)

### 2.- Listar repositorios
``` ruby 
helm repo list
```
![listarRepo](https://github.com/anasalasro/Kubernetes-Helm/blob/main/imagenes/listarRepo.png)

### 3.- Quitar repositorios.

``` ruby 
helm repo remove stable
```
### 4.- Buscar cahrts en repositorios
``` ruby
usuario@debian216:~$ helm search repo nginx

NAME                            	CHART VERSION	APP VERSION	DESCRIPTION                                       
bitnami/nginx                   	9.7.5        	1.21.6     	NGINX Open Source is a web server that can be a...
bitnami/nginx-ingress-controller	9.1.5        	1.1.1      	NGINX Ingress Controller is an Ingress controll...
bitnami/nginx-intel             	0.1.1        	0.4.7      	NGINX Open Source for Intel is a lightweight se...
stable/nginx-ingress            	1.41.3       	v0.34.1    	DEPRECATED! An nginx Ingress controller that us...
stable/nginx-ldapauth-proxy     	0.1.6        	1.13.5     	DEPRECATED - nginx proxy with ldapauth            
stable/nginx-lego               	0.3.1        	           	Chart for nginx-ingress-controller and kube-lego  
bitnami/kong                    	5.0.2        	2.7.0      	Kong is a scalable, open source API layer (aka ...
stable/gcloud-endpoints         	0.1.2        	1          	DEPRECATED Develop, deploy, protect and monitor...

usuario@debian216:~$ helm search repo wordpress

NAME             	CHART VERSION	APP VERSION	DESCRIPTION                                       
bitnami/wordpress	13.0.6       	5.8.3      	WordPress is the world's most popular blogging ...
stable/wordpress 	9.0.3        	5.3.2      	DEPRECATED Web publishing platform for building...

```
