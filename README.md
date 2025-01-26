# prometheus-grafana-kubernates-monitorning
This repository provides the setup and configuration for integrating Prometheus and Grafana with Kubernetes to monitor and visualize containerized applications and infrastructure metrics.
Prometheus and Grafana Kubernetes Monitoring

This repository provides a comprehensive guide to set up Prometheus and Grafana for monitoring and visualizing Kubernetes clusters. Prometheus is used for collecting and storing metrics, while Grafana is used to create dashboards for visualizing those metrics.

## Prerequisites

Kubernetes cluster (local or cloud-based)

kubectl CLI tool installed

Helm installed (for easy deployment)


## Steps to Integrate Prometheus and Grafana with Kubernetes

Step 1: Install Prometheus using Helm

    1. Add the Prometheus Helm chart repository:
    
    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
    helm repo update
    
    
    2. Install Prometheus on your Kubernetes cluster:
    
    helm install prometheus prometheus-community/prometheus
    
    
    3. Verify that Prometheus is installed:
    
    kubectl get pods -n default
    


Step 2: Install Grafana using Helm

    1. Add the Grafana Helm chart repository:
    
    helm repo add grafana https://grafana.github.io/helm-charts
    helm repo update
    
    
    2. Install Grafana on your Kubernetes cluster:
    
    helm install grafana grafana/grafana
    
    
    3. Verify that Grafana is installed:
    
    kubectl get pods -n default



Step 3: Access Grafana Dashboard

    1. To access Grafana's UI, port-forward the Grafana pod:
    
    kubectl port-forward svc/grafana 3000:80
    
    
    2. Open your browser and go to http://localhost:3000. The default login credentials are:
    
    Username: admin
    
    Password: prom-operator (or check the password using kubectl get secret)
    



Step 4: Configure Prometheus as Data Source in Grafana

    1. Once logged in to Grafana, click on the gear icon (⚙️) in the left sidebar, then select Data Sources.
    
    
    2. Click Add data source and select Prometheus.
    
    
    3. In the URL field, enter the URL for Prometheus (usually http://prometheus-server.default.svc.cluster.local:80).
    
    
    4. Click Save & Test to verify the connection.
    


Step 5: Import Kubernetes Dashboards in Grafana

    1. In Grafana, go to the Dashboard section and click + Create.
    
    
    2. Select Import and enter the dashboard ID for Kubernetes (e.g., 315 for the Kubernetes Cluster Monitoring dashboard).
    
    
    3. Click Load and choose the Prometheus data source you just configured.
    


Step 6: Verify Metrics

    Grafana will now display a variety of Kubernetes metrics including CPU, memory usage, and pod health.
    
    You can explore and customize the dashboards based on the metrics you want to visualize.


## Conclusion

You have successfully set up Prometheus and Grafana on your Kubernetes cluster to monitor and visualize the metrics from your containerized applications. Grafana provides a powerful interface for creating custom dashboards to keep track of system health, performance, and other key metrics.
