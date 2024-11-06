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

3. Verify Pod and Service Status:

```
kubectl get pods -n newelasticstackdeployment
kubectl get svc -n newelasticstackdeployment
```

4. Port Forward Kibana to Localhost:

```
kubectl port-forward service/kibana 5601:5601 -n newelasticstackdeployment
```

Access Kibana Dashboard
Once port forwarding is set up, you can access the Kibana dashboard by navigating to <http://localhost:5601> in your web browser.
