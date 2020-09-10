1. Install minikube:
  Run command:
    ```none
    curl -Lo minikube https://storage.googleapis.com/minikube/releases/v1.13.0/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
    ```

## K8S with minikube
  1. Create cluster
    - Run command: 
      ```none
      minikube version
      ```
      ```none
      minikube start
      ```
  2. Deployment \
    - Run command:
      ```none
      kubectl create deployment $DEPLOY_NAME --image=$IMAGE_URL
      ```
    - Get list deployments:
      ```none
      kubectl get deployments
      ```
  3. Create service \
    - expose port
  
