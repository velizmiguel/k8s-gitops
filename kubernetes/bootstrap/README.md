# k8s-gitops


## Bootstrap Flux:

flux bootstrap github \
  --token-auth \
  --owner=velizmiguel \
  --repository=k8s-gitops \
  --branch=main \
  --path=kubernetes/bootstrap \
  --personal


