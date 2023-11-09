# Bootstrap


## Bootstrap Flux:

flux bootstrap github \
  --token-auth \
  --owner=velizmiguel \
  --repository=k8s-gitops \
  --branch=main \
  --path=kubernetes/bootstrap \
  --personal


## Apply Cluster Configuration

_These cannot be applied with `kubectl` in the regular fashion due to be encrypted with sops_

```sh
sops --decrypt kubernetes/bootstrap/flux-system/age-key.sops.yaml | kubectl apply -f -
sops --decrypt kubernetes/flux/vars/vault-secrets.sops.yaml | kubectl apply -f -
```
