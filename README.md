# recognition-model-helm
Repository holding `Helm` code for deploying cars recognition model on Kubernetes cluster (e.g. `minikube`). 

# Image Classification Model
Mentioned model is avaliable:
- [on Roboflow](https://universe.roboflow.com/tarik-yilmaz-kanzileri/detection-f1-cars),
- [on GitHub](https://github.com/azawalich/formula-one-recognition-model),
- [on GitLab](https://gitlab.com/formula-1-fullstack-mlops/formula-one-recognition-model).

# Adding image to use in minikube
`minikube image load f1-recognition-model:v0.4`

# Execution steps 
## 0. RUNNING MINIKUBE LOCAL CLUSTER ##
0.1. `minikube start`
```
😄  minikube v1.32.0 on Ubuntu 19.10
✨  Using the docker driver based on existing profile
💨  For improved Docker performance, Upgrade Docker to a newer version (Minimum recommended version is 20.10.0, minimum supported version is 18.09.0, current version is 19.03.8)
👍  Starting control plane node minikube in cluster minikube
🚜  Pulling base image ...
🏃  Updating the running docker "minikube" container ...
🐳  Preparing Kubernetes v1.28.3 on Docker 24.0.7 ...
🔎  Verifying Kubernetes components...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🌟  Enabled addons: storage-provisioner, default-storageclass

❗  /usr/bin/kubectl is version 1.18.0, which may have incompatibilities with Kubernetes 1.28.3.
    ▪ Want kubectl v1.28.3? Try 'minikube kubectl -- get pods -A'
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
```
0.2. `minikube dashboard`
```
🔌  Enabling dashboard ...
    ▪ Using image docker.io/kubernetesui/dashboard:v2.7.0
    ▪ Using image docker.io/kubernetesui/metrics-scraper:v1.0.8
💡  Some dashboard features require the metrics-server addon. To enable all features please run:

        minikube addons enable metrics-server


🤔  Verifying dashboard health ...
🚀  Launching proxy ...
🤔  Verifying proxy health ...
🎉  Opening http://127.0.0.1:43709/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/ in your default browser...
Opening in existing browser session.
```
0.3 `minikube addons enable ingress`
```
💡  ingress is an addon maintained by Kubernetes. For any concerns contact minikube on GitHub.
You can view the list of minikube maintainers at: https://github.com/kubernetes/minikube/blob/master/OWNERS
    ▪ Using image registry.k8s.io/ingress-nginx/controller:v1.9.4
    ▪ Using image registry.k8s.io/ingress-nginx/kube-webhook-certgen:v20231011-8b53cabe0
    ▪ Using image registry.k8s.io/ingress-nginx/kube-webhook-certgen:v20231011-8b53cabe0
🔎  Verifying ingress addon...
🌟  The 'ingress' addon is enabled
```

## 1. INSTALLING HELM CHART ##
`helm install recognition-model ./recognition-model-helm/`
```
# Output:
# NAME: recognition-model
# LAST DEPLOYED: Thu Apr 11 02:03:10 2024
# NAMESPACE: default
# STATUS: deployed
# REVISION: 1
# TEST SUITE: None
```

## 2. UNINSTALLING HELM CHART ##
`helm uninstall recognition-model`