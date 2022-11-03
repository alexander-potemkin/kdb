# Kubernetes

# K8s limits

as per [the doc](https://kubernetes.io/docs/setup/best-practices/cluster-large/).

<aside>
💡 - No more than 110 pods per node ⇒ ≤~100 user containers per server
- No more than 5 000 nodes ⇒ servers
- No more than 150 000 total pods ⇒ doesn't make much sense for now
- No more than 300 000 total containers ⇒ ≤ 300K user containers

</aside>

# Troubleshooting guide

See Kube events - please, note they are *not* synchronized - pay attention to the even age - first symbols - you need: '*0s*' only.

```bash
kubectl --kubeconfig kubeconfig.service-cluster get ev -w #shows only cluster events
kubectl --kubeconfig kubeconfig.service-cluster -n infra get ev -w #inside kube inside namespace
```

Get **nodes** status

```bash
kubectl --kubeconfig kubeconfig.service-cluster top nodes
```

See **pods** in a specific namespace

```bash
kubectl --kubeconfig kubeconfig.service-cluster -n infra get pods
```

Check **volumes** at specific *namespace*

```bash
kubectl --kubeconfig kubeconfig.service-cluster -n infra describe pvc
```

Check specific **pod**

```bash
kubectl --kubeconfig kubeconfig.service-cluster -n infra describe pod security-master-0
```

Check **pod logs**

```bash
kubectl --kubeconfig kubeconfig.service-cluster -n infra logs security-master-0
```

Get load balancer IP

```bash
kubectl --kubeconfig kubeconfig -n ingress-nginx get svc | grep LoadBalancer | awk '{print $4}'
```

Delete specific pod(s)

```bash
kubectl --kubeconfig kubeconfig.service-cluster -n infra delete pod security-master-0 security-master-1 security-master-2
```

# Installation guide

Kubernetes install on Ubuntu

sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl
sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg [https://packages.cloud.google.com/apt/doc/apt-key.gpg](https://packages.cloud.google.com/apt/doc/apt-key.gpg)
echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] [https://apt.kubernetes.io/](https://apt.kubernetes.io/) kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl

Terraform install on Ubuntu

curl -fsSL [https://apt.releases.hashicorp.com/gpg](https://apt.releases.hashicorp.com/gpg) | sudo apt-key add -
sudo apt-add-repository "deb [arch=$(dpkg --print-architecture)] [https://apt.releases.hashicorp.com](https://apt.releases.hashicorp.com/) $(lsb_release -cs) main"
sudo apt install terraform

Helm on Ubuntu

curl [https://baltocdn.com/helm/signing.asc](https://baltocdn.com/helm/signing.asc) | sudo apt-key add -
sudo apt-get install apt-transport-https --yes
echo "deb [https://baltocdn.com/helm/stable/debian/](https://baltocdn.com/helm/stable/debian/) all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm