# AJ Portfolio

## Setup

1. Make sure you have all the files below:

   - ./secrets.yaml
   - ./config/wordpress/wp-config.php
   - ./config/react/local.js

2. Setup secrets:

   - Passwords: `kubectl create -f ./secrets.yaml`
   - Database: `kubectl create secret generic database --from-file=config=./config/database/aj_portfolio.sql`
   - Backend: `kubectl create secret generic backend --from-file=config=./config/backend/wp-config.php`
   - Frontend: `kubectl create secret generic frontend --from-file=config=./config/frontend/local.js`

3. Setup persistent volumes: `kubectl create -f ./pvc.yaml`

4. Setup frontend: `kubectl create -f ./frontend.yaml`

   - If you get a PostStartHookError, just wait unless it says “CrashLoopBackOff”

5. Setup database: `kubectl create -f ./database.yaml`

6. Setup backend: `kubectl create -f ./backend.yaml`

   - If you get a PostStartHookError, just wait unless it says “CrashLoopBackOff”

## First time setup

1. Go through all the setup steps first

2. Initialize database:

   More info coming soon

   - Get all pods running: `kubectl get pods`
   - Look for the pod name that starts with "database-deployment-..."
   - Go into the pod: `kubectl exec -it database-deployment-... bash`
   - Login to mysql: `mysql -u USERNAME -pPASSWORD`
   - Select database: `use aj_portfolio;`
   - Source the SQL file: `source /opt/app/aj_portfolio/config/mysql/aj_portfolio.sql;`

3. Initialize wordpress uploads:
