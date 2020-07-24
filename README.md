# apiportal.mplatform.com

apiportal is the Drupal apigee kickstart web interface.

## Installation

```bash
For Helm version 3.1.2 run the following;
kubectl create ns api-portal
helm install --namespace api-portal qa-apiportal -f ./helm-apiportal/qa-values.yaml ./helm-apiportal

For Helm version 3.2.4 use the following;
dev helm install --create-namespace dev-apiportal ./helm-apiportal
qa  helm install --create-namespace qa-apiportal -f ./helm-apiportal/qa-values.yaml ./helm-apiportal
int  helm install --create-namespace int-apiportal -f ./helm-apiportal/int-values.yaml ./helm-apiportal
prod helm install --create-namespace prod-apiportal -f ./helm-apiportal/prod-values.yaml ./helm-apiportal

upgrade int helm upgrade int-apiportal -f ./helm-apiportal/int-values.yaml ./helm-apiportal
```
## Creating the secret

The secret name is specified in deployment and must match **drupalsecret**.
Check for secret existence before deployment with;
kubectl get secret drupalsecret --output=yaml


kubectl create secret docker-registry drupalsecret \\  
--docker-server=https://index.docker.io/v1/ \\  
--docker-username=request \\  
--docker-password=request \\  
--docker-email=Markus.plattner@xaxis.com \\  
--namespace api-portal -o yaml > drupal-secret.yaml


## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.


Please make sure to update tests as appropriate.

## License
[GroupM](https://www.groupm.com)