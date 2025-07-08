# Elasticsearch-Logstash-Kibana (ELK Stack) on Kubernetes

This repository provides Kubernetes deployment configurations for the ELK stack (Elasticsearch, Logstash, Kibana). It offers two main deployment options:

- `elk.yml`: Deploys Elasticsearch, Logstash, and Kibana. This is suitable for basic logging setups where you might forward logs directly to Logstash or use another log shipper.
- `elkb.yml`: Deploys Elasticsearch, Logstash, Kibana, and Filebeat. This is a more complete solution for collecting logs directly from Kubernetes nodes or applications using Filebeat.

## Setup Process

### Prerequisites

Before you begin, ensure you have the following installed:

- **kubectl**: The Kubernetes command-line tool.
- A running Kubernetes cluster (e.g., Minikube, Docker Desktop with Kubernetes enabled, or a cloud-based cluster).

### Deployment Steps

1.  **Choose your deployment file**:
    - For Elasticsearch, Logstash, and Kibana only: `elk.yml`
    - For Elasticsearch, Logstash, Kibana, and Filebeat: `elkb.yml`

2.  **Create a Kubernetes Namespace**:
    It's recommended to deploy the ELK stack into its own namespace.
    ```bash
    kubectl create namespace newelasticstackdeployment
    ```

3.  **Apply the Kubernetes Configuration**:
    Apply the chosen YAML file to your Kubernetes cluster.
    ```bash
    # If using elk.yml
    kubectl apply -f elk.yml

    # If using elkb.yml
    kubectl apply -f elkb.yml
    ```

4.  **Verify Pod and Service Status**:
    Check if the pods and services are running correctly in your namespace.
    ```bash
    kubectl get pods -n newelasticstackdeployment
    kubectl get svc -n newelasticstackdeployment
    ```
    Ensure all pods are in a `Running` state.

5.  **Port Forward Kibana to Localhost**:
    To access the Kibana dashboard from your local machine, set up port forwarding.
    ```bash
    kubectl port-forward service/kibana 5601:5601 -n newelasticstackdeployment
    ```
    This command will block your terminal. You can run it in a separate terminal session or in the background.

### Access Kibana Dashboard

Once port forwarding is set up, you can access the Kibana dashboard by navigating to <http://localhost:5601> in your web browser.

## Project Structure

- `elk.yml`: Kubernetes manifests for Elasticsearch, Logstash, and Kibana.
- `elkb.yml`: Kubernetes manifests for Elasticsearch, Logstash, Kibana, and Filebeat (including Filebeat configuration).
- `README.md`: This documentation file.
