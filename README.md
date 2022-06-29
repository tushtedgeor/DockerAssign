Project Title: Docker Assignment
Project Description: I have tried building two docker containers within same network with reverse proxy with certain restrictions and specifications.
Procedure: -> First container with the create react App. Installed NodeJs and npm in my directory with npx create-react-app sampApp command in the terminal.
           ->In the next step I have pulled NGINX latest image from the docker hub. Copied or mounted the build directory to the NGINX docker container by the command: COPY ./build/usr/share/nginx/html/index.html in a dockerfile.
           ->Then I have build the image from the dockerfile with the command: sudo docker build -t weberver, webserver being the tag of my image.
           ->Finally, I have build my first docker container with the command: sudo docker run -it -d -p 8080:80 --name reactcontain webserver, reactconatiner being the name of my container and webserver being the image from it is being built.
           -> For the second container, I have formed another docker file according to the given specifications, installed nginx in the base image ubuntu, and then enabled nginx to capture the clients IP in the access logs and then pointing the access and the error logs to the docker stdout/stderr respectively, exposing port 80 for the nginx webserver.
           ->Again formed the image and then my reverse proxy second container.
           
           
 Procedure to bring both the containers in the same network:- I have made a docker compose file with both my conatainers where i have protected the first container from the outside world by specifying port with 127.0.0.1:8080:80 therby restricting the access. The dockercompose file itself takes the responsibility of not only building the containers but also enables both the containers to come in the same network.
 
 Procedure to make Nginx reverse proxy: The proxy_pass setting makes the Nginx reverse proxy setup to work. To setup the Nginx proxy_pass globally, I have edited the default file in NGINX sites-avaiable folder by the command: sudo nano /etc/nginx/conf.d/default.conf where i have added the location setting. Copied this Nginx default file to my second container which is to behave as the reverse proxy.
