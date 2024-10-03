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

2. Deployment

   - Run command:

     ```none
     kubectl create deployment $DEPLOY_NAME --image=$IMAGE_URL
     ```

     - Get list deployments:

     ```none
     kubectl get deployments
     ```

3. Create service

   - expose port:

   ```none
   kubectl expose deployment $DEPLOY_NAME --type=$TYPE --port=$PORT
   ```

   - Get link access on browser

   ```none
   minikube service $DEPLOY_NAME
   ```

---

## Bugs

1. Internal error occurred: failed calling webhook "validate.nginx.ingress.kubernetes.io": \
   run command:

   ```none
   kubectl delete -A ValidatingWebhookConfiguration ingress-nginx-admission
   ```

2. Run local: change domain to:
   - .local
   - .localhost
   - .test
   - (any custom/non-standard top-level domain)
3. Remove service
   - systemctl stop {service}
   - yum remove {service}
   - systemctl daemon-reload
   - systemctl reset-failed

---

## Monitor

1. Check CRIO cgroup:

   ```none
   cat /etc/crio/crio.conf | grep cgroup
   ```

## Mongo command

1. Mongo dump
```sh
mongodump -u [DB_USERNAME] --db [DB_DATABASE] --authenticationDatabase=admin --gzip --archive > /path/to/file/dump_`date "+%Y-%m-%d"`.gz
```

2. Copy file remote machine to local computer

```sh
scp -P [port] [user]@[server_id]:/path/to/file /path/to/local
```

3. Mongo restore

```sh
mongorestore -u [DB_USERNAME] --authenticationDatabase=admin --gzip --archive=/path/to/file/dump_2024-10-03.gz --db [DB_DATABASE]
```
