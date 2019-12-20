# Monitoring k8s cluster with Prometheus from outside

In a production setup its never advisable to install monitoring tool on the same infra/platform that is being monitored.

To monitor k8s with Prometheus it must be installed outside of the cluster

# Setup

* Run minikube, this code assumes its being run on 192.168.99.114, change in files in resources folder as per your IP
* Place ca.crt of your cluster in the resoruces folder
* kubectl apply -f "all yml files in resources folder".  It will create service account, cluster role and cluster binding for the user Prometheus will use to make API calls to k8s
 * Execute docker-compose up -d to start prometheus
