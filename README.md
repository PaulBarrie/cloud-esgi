# ESGI Cloud project - AL

*Auteur: BARRIÉ Paul - BENADJAOUD Wissam - NGUYEN Ifzas*

>## Déploiement du projet
Prérequis: *kubectl*, *gcloud*, *helm*.

On suppose que vous disposez d'un cluster GKE et que la kubeconfig du cluster a été importée (si non `gcloud container clusters get-credentials <cluster-name>`).


Tout d'abord, il faut créer une addresse statique régionale que l'on va assigner à notre ingress. Pour cela, lancez:

```
    gcloud compute addresses <addresse_name> --region=<region_cluster>
```

Ensuite, il faut instaler l'ingress controller nginx de la manière suivante:

```
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update

helm install --set controller.service.loadBalancerIP=<ip> nginx-ingress ingress-nginx/ingress-nginx
```

Vous pouvez ensuite appliquer les configurations kubernetes:

```
    kubectl apply -f kube-manifest
```

Les différents service seront disponibles à:

* `ip` pour la console d'administration keycloak
* `ip/app` pour le front
* `ip/app` pour l'API
