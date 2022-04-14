### Usage

1. Clone the repo
   ```sh
   git clone https://github.com/batuhanakca/notejam-k8s.git
   ```
2. If you are using minikube or local k8s installation run below commands to deploy the application on k8s
   ```sh
   kubectl apply -f kubernetes/deployment.yml
   kubectl apply -f kubernetes/service.yml.minikube
   kubectl apply -f kubernetes/hpa.yml
   kubectl port-forward svc/notejam 5000:5000
   ```
   Then on your browser type
   ```
   localhost:5000
   ```
3. To create GKE (Google Kubernetes Engine) nodes with terraform, you can use either files under `autopilot-terraform` or `gke-basic-terraform` for standartd mode.
   e.g:
   ```sh
   cd autopilot-terraform/
   terraform init -upgrade
   terraform plan
   #ignore the Warning
   terraform apply
   ```
   To reach correct k8s cluster run below command 
   ```sh
   gcloud container clusters get-credentials $(terraform output -raw kubernetes_cluster_name) --region $(terraform output -raw region)
   ```
4. Then apply below yaml files to deploy the application
   ```sh
   kubectl apply -f kubernetes/deployment.yml
   kubectl apply -f kubernetes/service.yml.LoadB
   ```
5. If you are using Managed Cloud Environment, run below command and notedown External IP :
   ```
   kubectl get svc
   ```
   Then connect to that IP address on your browser. (default port 80)
