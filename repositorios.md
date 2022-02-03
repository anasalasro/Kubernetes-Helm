
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
