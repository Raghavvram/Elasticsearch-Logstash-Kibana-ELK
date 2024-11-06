# Elasticsearch-Logstash-Kibana (ELK Stack)
A Kubernetes deployment of Elastic Search, Log Stash, Kinana, File Beats (optional)


Commands to Apply Configuration and Port Forward

1. Create Namespace:

```
kubectl create namespace newelasticstackdeployment
```

2. Apply the Combined YAML File:

```
kubectl apply -f elk.yml
```
