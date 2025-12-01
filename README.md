# GOIT ARGO — GitOps Deployment with ArgoCD + AWS EKS

## 1. Deploy ArgoCD via Terraform
cd terraform/argocd
terraform init
terraform apply -auto-approve

kubectl get pods -n infra-tools

## 2. Access ArgoCD UI
kubectl port-forward svc/argocd-server -n infra-tools 8080:80

http://localhost:8080

kubectl -n infra-tools get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

## 3. Add Git repository
argocd repo add https://github.com/YOUR-USER/goit-argo --insecure-skip-server-verification

## 4. Verify Deployment
kubectl get pods -n application

## 5. Access nginx
kubectl port-forward svc/nginx -n application 8081:80

http://localhost:8081
