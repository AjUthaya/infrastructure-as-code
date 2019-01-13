# AJ Portfolio

### Setup

1. Make sure you have all the files below:

   - ./secrets.yaml
   - ./config/wordpress/wp-config.php
   - ./config/react/local.js

2. Setup config maps, run the following commands:

   - nginx: `kubectl create configmap nginx --from-file=config=./config/nginx/default.conf`

3. Setup secrets, run the following commands:

   - mysql: `kubectl apply -f ./secrets.yaml`
   - wordpress: `kubectl create secret generic wordpress --from-file=config=./config/wordpress/wp-config.php`
   - react: `kubectl create secret generic react --from-file=config=./config/react/local.js`

4. Setup persistent volume claims, run `kubectl apply -f ./pvc.yaml`

5. Setup backend deployments and services, run `kubectl create -f ./backend.yaml`

6. Run `kubectl get pods` and copy one of the names that start with "backend-deployment-..."

7. Run `kubectl exec -it backend-deployment-... bash` to go into a pod

8. Then run `cd /opt/app/aj_portfolio` (persistent storage location) and run the following commands:

   - `git clone https://github.com/AjUthaya/aj_portfolio-frontend-react.git`
   - `git clone https://github.com/AjUthaya/aj_portfolio-backend-wordpress.git`

9. Move config into repos, run the following commands:

   - Backend: `cp /opt/app/aj_portfolio/config/wordpress/wp-config.php /opt/app/aj_portfolio/aj_portfolio-backend-wordpress/wp-config.php`
   - Frontend: `cp /opt/app/aj_portfolio/config/react/local.js /opt/app/aj_portfolio/aj_portfolio-frontend-react/local.js`

10. Clean out nginx defaul files, run `rm -R /usr/share/nginx/html/*`

11. Move project into nginx view folder, run `cp /opt/app/aj_portfolio/aj_portfolio-backend-wordpress/* /usr/share/nginx/html/`
