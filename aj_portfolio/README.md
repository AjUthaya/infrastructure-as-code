# AJ Portfolio

### Setup

1. Make sure you have all the files below:

   - ./secret.yaml
   - ./config/wordpress/wp-config.php
   - ./config/react/local.js

2. Run `kubectl create configmap config --from-file=nginx=./config/nginx/default.conf` to store the file in kubernetes as a config map

3. Run `kubectl create secret generic config --from-file=react=./config/react/local.js --from-file=wordpress=./config/wordpress/wp-config.php` to store the config files as secrets in kubernetes

4. Run `kubectl create -f ./secret.yaml` to create secrets in kubernetes

5. Run `kubectl create -f ./pvc.yaml` to create a persistent storage claim in kubernetes

6. Run `kubectl create -f ./backend.yaml` to start up the backend in kubernetes
