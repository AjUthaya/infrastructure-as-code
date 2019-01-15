# AJ Portfolio

## Setup

1. Make sure you have all the files below:

   - ./secrets.yaml
   - ./config/wordpress/wp-config.php
   - ./config/react/local.js

2. Setup secrets, run the following commands:

   - mysql: `kubectl apply -f ./secrets.yaml`
   - wordpress: `kubectl create secret generic wordpress --from-file=config=./config/wordpress/wp-config.php`
   - react: `kubectl create secret generic react --from-file=config=./config/react/local.js`

3. Setup persistent volume claims, run `kubectl apply -f ./pvc.yaml`

4. Setup backend deployments and services, run `kubectl create -f ./backend.yaml`
