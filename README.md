Prerequisites::
Docker and Docker-compose should be insatalled in the host machine
Step1: Clone the repo
Step2: Run the below commands to create volume in your host machine.

  mkdir -p ./registry/auth
  mkdir -p ./registry/data



Step3: Run the below command to set the login username and password.
user  password
docker run --rm httpd:2 htpasswd -Bbn admin admin > ./registry/auth/htpasswd
** in above command change the user, here is admin to whatever you want and password here is admin change it to whatever you want **
Step4: Also change this username and password in compose.yml file.
it will show like this find below lines in compose file and change as per your requirments
**    - REGISTRY_AUTH_USERNAME=admin
- REGISTRY_AUTH_PASSWORD=admin  **
Step5: You need to chnage the url as per your domain or ip in the compose file below is the details where you need to chnage that.

  - NGINX_PROXY_PASS_URL=http://ip of your server or dns:5000  # URL of the registry server


Step6: Now it is time to see the magic just run the below command
docker compose up --build -d
Great work!!🚀 You finally setup the registry by yourself. So be proud of yourself 😊
