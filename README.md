# Prerequisites #

## Install Helm ##

```bash
$ kubectl apply -f helm-rbac.yaml
$ helm init --service-account tiller
```

## Install Cert-Manager ##

```bash
$ helm install stable/cert-manager --name cert-manager \
  --set ingressShim.defaultIssuerName=letsencrypt-prod \
  --set ingressShim.defaultIssuerKind=ClusterIssuer
```

## Adjust variables in YAML files ##

```
EMAIL - your email adress for Let's Encrypt
DOMAIN - your domain to be secured by SSL
TENANT_ID - Azure tenant ID
APPLICATION_ID - Azure app ID
APPLICATION_KEY - Azure app secret
BASE64_ENCODED_CUSTOM_SECRET - a custom secret for the "secure cookie", Base64-encoded
```

## Install sample ##

```bash
$ kubectl apply -f cert-issuer.yaml
$ kubectl apply -f certificate.yaml
$ kubectl apply -f oauth-proxy.yaml
$ kubectl apply -f service-deployment.yaml
$ kubectl apply -f oauth-proxy.yaml
```

# Documentation of OAuth2-Proxy #

<https://github.com/bitly/oauth2_proxy>