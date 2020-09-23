# Jetcare Deploy To Production Environment

> Namespace: `jetcare`. \
> Follow step-by-step \
> Make sure that you have: Helm v3 [installed](https://helm.sh/docs/using_helm/#installing-helm)

## List install:

- [Traefik](./traefik)
- [nats](./nats)
- [redis](./redis)
- [certs](./certs)

## Namespace

- Note: {namespace} = name given by you. ex: default, jetcare, ...

## secrets

> Create encoded secret by using this command: echo -n YOUR_SECRET_KEY | base64

## jwt secrets

```none
kubectl create secret generic jwt-key --from-file=/path/to/jwt_public.key --from-file=/path/to/jwt_private.key
```

## Docker container registry secret

> use for pull image from github packages

```none
kubectl create secret docker-registry <your_secret_name> \
  --docker-server=https://docker.pkg.github.com \
  --docker-username=<github_username> \
  --docker-password=<github_secret> \
  --docker-email=<email>
```

## Step-by-step deploy

1. Clone source from github.com
2. Push to branch `prod`
3. Get new version package
4. Run helm install with params version

## Deploy with helm v3+

> at root path project, run command

```none
helm upgrade --install default --namespace default ./packages/helm-charts --values=./packages/helm-charts/values_jck8s.yaml --set admin.image.version=prod-9d478ce --set backend.image.version=prod-9d478ce
```
