# Traefik:

**Add Traefik's chart repository to Helm:**

```none
helm repo add traefik https://containous.github.io/traefik-helm-chart
```

**Update the chart repository:**

```none
helm repo update
```

**Deploying traefik:**

> Exists: upgrade \
> Not Exists: install

```none
helm upgrade --install traefik traefik/traefik --set="additionalArguments={--providers.kubernetesingress,--entryPoints.websecure.http.tls=true}" --set="autoscaling.enabled=true" --set="autoscaling.minReplicas=2" --set="autoscaling.maxReplicas=10"
```

**Exposing the Traefik dashboard**

```none
kubectl port-forward $(kubectl get pods --selector "app.kubernetes.io/name=traefik" --output=name) 9000:9000
```

Accessible with the url: [http://127.0.0.1:9000/dashboard/](http://127.0.0.1:9000/dashboard/)

**Install Middlewares**

- https redirect

File: `/packages/cluster/k8s/traefik/middlewares/https-redirect-middleware.yaml`

```yaml
apiVersion: traefik.containo.us/v1alpha1
kind: Middleware
metadata:
  name: traefik-https-redirect
spec:
  redirectScheme:
    scheme: https
    permanent: true
    port: 443
```

Apply:

```none
kubectl apply -f https-redirect-middleware.yaml
```

- basic auth

File: `basic-auth-middleware.yaml`

```yaml
apiVersion: traefik.containo.us/v1alpha1
kind: Middleware
metadata:
  name: traefik-basic-auth
spec:
  basicAuth:
    secret: traefik-basic-auth
```

Apply:

```none
kubectl apply -f basic-auth-middleware.yaml
```
