# Monitoring k8s cluster with Prometheus from outside

In a production setup its never advisable to install monitoring tool on the same infra/platform that is being monitored.

To monitor k8s with Prometheus it must be installed outside of the cluster since if k8s cluster goes down then it leaves the support personnel  in dark to look for problem.

# Setup

* Run minikube, this code assumes its being run on 192.168.99.114, change in files in resources folder as per your IP

* Place ca.crt of your cluster in the resoruces folder

* Create service account, cluster role  for the user Prometheus will use to make API calls to k8s

```
kubectl apply -f "all yml files in resources folder" 
``` 

* For cluster role binding, execute 
```
kubectl create clusterrolebinding prometheus-querier --clusterrole=prometheus --serviceaccount=kube-system:prometheus
```

 * Execute docker-compose up -d to start prometheus
