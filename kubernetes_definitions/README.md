folder contains information for the k8s cluster definition

### steps to login to AWS using minkube from local desktop 
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 084828572941.dkr.ecr.us-east-1.amazonaws.com


kubectl create secret docker-registry aws-ecr-secrets \
  --docker-server=084828572941.dkr.ecr.us-east-1.amazonaws.com \
  --docker-username=AWS \
  --docker-password=$(aws ecr get-login-password --region us-east-1)

### Check pods database
kubectl exec -it <mysql-pod-name> -n <namespace> -- mysql -u<username> -p
 - "SHOW DATABASES;"

### Commands
kubectl exec -it <nginx-pod-name> -- nginx -t
kubectl get svc nginx-service -o yaml
kubectl get pods --show-labels
