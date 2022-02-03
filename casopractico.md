### 1.- instalamos el chart de wordpress parametrizando el servicio y el nombre del blog:
```ruby
usuario@debian216:~$ helm install wordpress bitnami/wordpress --set service.type=NodePort --set wordpressBlogName="Wordpress de Ana"

NAME: wordpress
LAST DEPLOYED: Thu Feb  3 12:54:38 2022
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
CHART NAME: wordpress
CHART VERSION: 13.0.6
APP VERSION: 5.8.3

** Please be patient while the chart is being deployed **

Your WordPress site can be accessed through the following DNS name from within your cluster:

    wordpress.default.svc.cluster.local (port 80)

To access your WordPress site from outside the cluster follow the steps below:

1. Get the WordPress URL by running these commands:

   export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services wordpress)
   export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")
   echo "WordPress URL: http://$NODE_IP:$NODE_PORT/"
   echo "WordPress Admin URL: http://$NODE_IP:$NODE_PORT/admin"

2. Open a browser and access WordPress using the obtained URL.

3. Login with the following credentials below to see your blog:

  echo Username: user
  echo Password: $(kubectl get secret --namespace default wordpress -o jsonpath="{.data.wordpress-password}" | base64 --decode)
```
### 2.- Comprobamos todo lo que nos ha desplegado:
```ruby
usuario@debian216:~$ kubectl get all

NAME                             READY   STATUS             RESTARTS   AGE
pod/wordpress-5cbd46c5fd-7f8mb   0/1     ImagePullBackOff   0          105s
pod/wordpress-mariadb-0          0/1     ImagePullBackOff   0          105s

NAME                        TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
service/kubernetes          ClusterIP   10.96.0.1        <none>        443/TCP                      28h
service/wordpress           NodePort    10.110.230.250   <none>        80:31303/TCP,443:32687/TCP   105s
service/wordpress-mariadb   ClusterIP   10.105.237.238   <none>        3306/TCP                     105s

NAME                        READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/wordpress   0/1     1            0           105s

NAME                                   DESIRED   CURRENT   READY   AGE
replicaset.apps/wordpress-5cbd46c5fd   1         1         0       105s

NAME                                 READY   AGE
statefulset.apps/wordpress-mariadb   0/1     105s

```
### 3.- Comprobamos que podemos acceder a la aplicacion con la ip de minikube y el puerto que nos asigna el servicio:
``` ruby
usuario@debian216:~$ minikube ip
192.168.59.102

service/wordpress           NodePort    10.110.230.250   <none>        80:31303/TCP,443:32687/TCP   105s
```
![helm](https://github.com/anasalasro/Kubernetes-Helm/blob/main/imagenes/comprobacion.png)
