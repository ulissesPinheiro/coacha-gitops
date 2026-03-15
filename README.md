# coacha-gitops

Repositório GitOps do projeto **coacha** — contém apenas os manifests Kubernetes.

Monitorado pelo ArgoCD: qualquer push na branch `main` é automaticamente aplicado no cluster.

## Estrutura

```
k8s/
├── namespace.yaml     # Namespace coacha-app
├── configmap.yaml     # Configurações da aplicação
├── deployment.yaml    # Deployment + probes + resources
├── service.yaml       # ClusterIP service
├── ingress.yaml       # Ingress nginx (coacha.local)
├── hpa.yaml           # Horizontal Pod Autoscaler
└── argocd-app.yaml    # Application do ArgoCD
```

## ⚠️ Secret

O `secret.yaml` está no `.gitignore`. Criar manualmente:

```bash
kubectl create secret generic coacha-secrets \
  --from-literal=API_KEY=valor \
  --from-literal=DB_PASSWORD=valor \
  -n coacha-app
```

## Repositório da aplicação

[coacha](https://github.com/ulissesPinheiro/coacha) — código Java + Dockerfile
