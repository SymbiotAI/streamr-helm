
# Create a config

Create a config file for the Streamr node.
```bash
mkdir ~/.streamrDocker
sudo chmod -R 777 ~/.streamrDocker/
sudo docker run -it -v $(cd ~/.streamrDocker && pwd):/home/streamr/.streamr streamr/node bin/config-wizard
```

Create a new namespace
```bash
kubectl create namespace streamr
```

Create a secret in k8s with the config file
```bash
kubectl create secret generic streamr-config --from-file=default.json=$HOME/.streamrDocker/config/default.json --namespace streamr
```

# Apply helm chart

Apply the helm chart
```bash
helm upgrade --install streamr . --namespace streamr
```
