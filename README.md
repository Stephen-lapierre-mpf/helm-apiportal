# apiportal.mplatform.com

apiportal is the Drupal apigee kickstart web interface.

## Installation

```bash
dev helm install --create-namespace dev-apiportal ./helm-apiportal
qa  helm install --create-namespace qa-apiportal -f ./helm-apiportal/qa-values.yaml ./helm-apiportal
int  helm install --create-namespace int-apiportal -f ./helm-apiportal/int-values.yaml ./helm-apiportal
prod helm install --create-namespace prod-apiportal -f ./helm-apiportal/prod-values.yaml ./helm-apiportal
```


## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[GroupM](https://www.groupm.com)