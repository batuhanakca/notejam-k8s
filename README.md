### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/batuhanakca/notejam-k8s.git
   ```
2. if you are using minikube;
   ```sh
   kubectl apply -f deployment.yml
   kubectl apply -f service.yml.minikube
   kubectl apply -f hpa.yml
   kubectl port-forward svc/test1 5000:5000
   ```
3. Then on your browser type
   ```
   localhost:5000
   ```
4. If you will be using it on a Managed Cloud Environment, `use service.yml.LoadB` instead of `service.yml.minikube` and also you don't need to use port-forwarding in there.
