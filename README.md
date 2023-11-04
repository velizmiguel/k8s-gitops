# Bootstrap

## Talos

### Create Talos Secrets

```
talhelper gensecret > talsecret.sops.yaml
sops -e -i talsecret.sops.yaml
talhelper genconfig
export TALOSCONFIG=~/k8s-gitops/talos/clusterconfig/talosconfig
```

```
talosctl -n 10.0.10.81 apply-config --file clusterconfig/super-cluster-master-microserver-81.yaml --insecure
talosctl -n 10.0.0.82 apply-config --file clusterconfig/k8s-m1*.yaml --insecure
talosctl -n 10.0.0.83 apply-config --file clusterconfig/k8s-m2*.yaml --insecure
talosctl -n 10.0.0.84 apply-config --file clusterconfig/k8s-w0*.yaml --insecure
talosctl -n 10.0.0.85 apply-config --file clusterconfig/k8s-w1*.yaml --insecure
```

### Apply Bootstrap
`talosctl bootstrap --nodes 10.0.10.81 --endpoints 10.0.10.81 --talosconfig=./clusterconfig/talosconfig`

### Get kubeconfig file
`talosctl -n 10.0.10.81 --endpoints 10.0.10.81 --talosconfig=./clusterconfig/talosconfig kubeconfig`

### Get Dashboard
`talosctl -n 10.0.10.81 --endpoints 10.0.10.81 --talosconfig=./clusterconfig/talosconfig dashboard`

### Get Health 
`talosctl -n 10.0.10.81 --endpoints 10.0.10.81 --talosconfig=./clusterconfig/talosconfig dashboard`