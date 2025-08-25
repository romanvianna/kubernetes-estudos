# Criando Cluster Kind
kind create cluster --name=Local --config=cluster/mononode.yaml
# NGINX-INGRES
kubectl apply --filename https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/provider/kind/deploy.yaml
# CERT-MANAGER
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.18.2/cert-manager.yaml
kubectl get pods --namespace cert-manager --watch
# ARGOCD
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl apply -f argo/ingress.yaml
kubectl apply -f argo/app-of-apps.yaml
#
