# AJ Portfolio

## Setup

1. Make sure you have all the files below:

   - ./secrets.yaml
   - ./config/wordpress/wp-config.php
   - ./config/react/local.js

2. Setup secrets:

   - passwords: `kubectl apply -f ./secrets.yaml`
   - mysql: `kubectl create secret generic mysql --from-file=config=./config/mysql/aj_portfolio.sql`
   - wordpress: `kubectl create secret generic wordpress --from-file=config=./config/wordpress/wp-config.php`
   - react: `kubectl create secret generic react --from-file=config=./config/react/local.js`

3. Setup persistent volume claims: `kubectl apply -f ./pvc.yaml`

4. Setup database deployments and services: `kubectl create -f ./database.yaml`

5. Setup backend deployments and services: `kubectl create -f ./backend.yaml`

## First time setup

1. Go through all the setup steps first

2. Initialize database:

   - Get all pods running: `kubectl get pods`
   - Look for the pod name that starts with "database-deployment-..."
   - Go into the pod: `kubectl exec -it database-deployment-... bash`
   - Login to mysql: `mysql -u USERNAME -pPASSWORD`
   - Select database: `use aj_portfolio;`
   - Source the SQL file: `source /opt/app/aj_portfolio/config/mysql/database.sql;`

3. Initialize wordpress uploads:
