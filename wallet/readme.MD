
[app code](https://github.com/PabloMarrtinez/ssikit-incibe)

## UPLOAD A DOCKER IMAGES TO DOCKER HUB

```bash
docker-compose build
docker images
docker tag <id>  pablomarrtinez/wallet:<version>
docker push pablomarrtinez/wallet:<version>
```

## MINIKUBE DEPLOY

First steps:

1.  Add the fabric certs to `/shared` (needed if you want to use the not local version)

```bash
minikube start
minikube mount ./wallet/shared:/mnt/shared
minikube ip

helm delete wallet
helm install wallet wallet/
```

Tips: 

- You should use the IP provided by `minikube ip` and the ports that you specify in `values.yaml` to connect with the tool.

- You should add the next line to your `/etc/hosts`

```
<minikube_ip>	 umu-issuer umu-webWallet umu-verifier
```

- You have to accept the web certs manually:

```
https://umu-issuer:<issuer_port>
https://umu-webwallet:<web_wallet_port>
https://umu-verifier:<verifier_port>
```

## K3S DEPLOY