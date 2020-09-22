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
