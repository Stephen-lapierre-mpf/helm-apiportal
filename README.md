# apiportal.mplatform.com

apiportal is the Drupal apigee kickstart web interface.

## Installation

```bash
For Helm version 3.1.2 run the following;
kubectl create ns api-portal
helm install --namespace api-portal qa-apiportal -f ./helm-apiportal/qa-values.yaml ./helm-apiportal

For Helm version 3.2.4 use the following;
dev$ helm install --create-namespace dev-apiportal ./helm-apiportal
qa$  helm install --create-namespace qa-apiportal -f ./helm-apiportal/qa-values.yaml ./helm-apiportal
int$  helm install --create-namespace int-apiportal -f ./helm-apiportal/int-values.yaml ./helm-apiportal
prod$ helm install --create-namespace prod-apiportal -f ./helm-apiportal/prod-values.yaml ./helm-apiportal

upgrade int$ helm upgrade int-apiportal -f ./helm-apiportal/int-values.yaml ./helm-apiportal
```
## Creating the secret
This is the auth for image pull repo. If this is the internal environment
this would be the base64 encoded string for input;

{"auths":{"https://index.docker.io/v1/":{"username":"xaxisjenkins","password":"jenkins.xaxis",
"email":"Markus.plattner@xaxis.com","auth":"eGF4aXNqZW5raW5zOmplbmtpbnMueGF4aXM="}}}

This should be the string data for data named data for key named **getsecret** for the values file
for the current environment. Should be set before deployments in each value file. By default it is set to the Jenkins repo 
so should not need editing. This will enable the secret creation to be handled automatically. 
Deployment may fail if not set correct.
The secret name is specified in deployment and must match **drupalsecret**.

To create the correct string use;

kubectl create secret docker-registry drupalsecret \
--docker-server=https://index.docker.io/v1/ \
--docker-username=xaxisjenkins \
--docker-password=jenkins.xaxis \
--docker-email=Markus.plattner@xaxis.com \
--namespace api-portal -o yaml > docker-secret.yaml

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.


Please make sure to update tests as appropriate.

## License
[GroupM](https://www.groupm.com)