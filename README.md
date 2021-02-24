# Devops_Infra

# Deployment

## Kube-Prometheus

Kube-Prometheus est un opérateur Prometheus qui déploie Alertmanager, Node-Exporter, Prometheus et Grafana. L'opérateur original est trouvable à cette adresse : https://github.com/prometheus-operator/kube-prometheus.
La première étape consiste à déployer le dossier Setup.

```
cd kube-prometheus
kubectl create -f kube-prometheus/setup
```

Puis, il nous faut créer un secret. Ce secret contient les informations nécessaires à Prometheus pour qu'il puisse monitorer d'autres ressources que celles par défaut (Ici Jenkins). 

```
kubectl create secret generic -n monitoring additional-scrape-configs --from-file=prometheus-additional.yaml
```
On peut ensuite déployer le reste de l'opérateur.

```
kubectl create -f kube-prometheus/
```
