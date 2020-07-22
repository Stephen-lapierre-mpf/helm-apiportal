# apiportal.mplatform.com

apiportal is the Drupal apigee kickstart web interface.

## Installation

```bash
dev helm install --create-namespace dev-apiportal ./helm-apiportal
qa  helm install --create-namespace qa-apiportal -f ./helm-apiportal/qa-values.yaml ./helm-apiportal
int  helm install --create-namespace int-apiportal -f ./helm-apiportal/int-values.yaml ./helm-apiportal
prod helm install --create-namespace prod-apiportal -f ./helm-apiportal/prod-values.yaml ./helm-apiportal

upgrade int helm upgrade int-apiportal -f ./helm-apiportal/int-values.yaml ./helm-apiportal
```
## Creating the secret
The secret name is specified in deployment and must match "xaxissecret".

...bash
kubectl create secret docker-registry xaxissecret \
--docker-server=https://index.docker.io/v1/ \
--docker-username=request \
--docker-password=request \
--docker-email=Markus.plattner@xaxis.com \
--namespace api-portal -o yaml > xaxis-secret.yaml

kubectl get secret xaxissecret --output=yaml
...

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[GroupM](https://www.groupm.com)