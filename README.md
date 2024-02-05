Set up steps
1. Amazon EKS
Create an EKS cluster with suitable configuration hardware of worker node group.
Attach neccessary IAM roles for both EKS cluster and Node group.
Initialize connect between VS Code and Amazon EKS with the command below:
aws eks --region <YOUR_REGION> update-kubeconfig --name <YOUR_CLUSTER_NAME>
2. Amazon ECR
Set up an ECR for storing Docker images
3. Codebuild
Set up a Codebuild project with necessary IAM roles for CI with Github webhook events.
4. Database
Using Helm Chart to install and managed Postgresql
Set up Bitnami repo: 
helm repo add bitnami-repo https://charts.bitnami.com/bitnami
Install Postgresql with Helm Chart: 
helm install --set primary.persistence.enabled=false my-postgresql bitnami-repo/postgresql
Expose the password, connect to db and execute sample data in db folder.
5. Kubernetes deployment
Create configuration files (configmap.yml, deployment.yml, secret.yml, service.yml)
Using these commands to run the microservices as a pod in Kubernetes
kubectl apply -f deploy/secret.yml
kubectl apply -f deploy/configmap.yml
kubectl apply -f deploy/deployment.yml
kubectl apply -f deploy/service.yml
6. Application logs
Install Cloudwatch using cloudwatch-install.sh to enable application logging
Ensure the Database and microservices application is running and the database service is accessbile via the application.