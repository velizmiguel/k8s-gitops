# k8s-gitops


Good general command

```
kubectl api-resources --verbs=list --namespaced -o name \
  | xargs -n 1 kubectl get --show-kind --ignore-not-found -n rook-ceph
```

---

Setup SOPS:

```
/Users/miguel/Library/Application\ Support/sops/age/keys.txt

cat /Users/miguel/Library/Application\ Support/sops/age/keys.txt |
kubectl create secret generic sops-age \
--namespace=flux-system \
--from-file=age.agekey=/dev/stdin
```

Sample how to encrypt a file:
```
sops --age=age1rtcaj34psg3fgeepa5dfgxa2f5s7dyvt5sefnsaaq6zugzmgxpzsvjjzft --encrypt --encrypted-regex '^(data|stringData)$' --in-place basic-auth.yaml
```

And finally set the decryption secret in the Flux Kustomization to sops-age.