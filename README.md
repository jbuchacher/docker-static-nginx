1. git clone https://github.com/jbuchacher/docker-static-nginx.git
1. cd docker-static-nginx
1. docker build -t nginx .
1. docker run -d -p 80 --name nginx -v $PWD/website:/var/www/html/website nginx nginx
1. export fancyport=$(docker port nginx | awk -F':' '{ print $NF }')
1. curl $(docker-machine ip dev):$fancyport
1. VBoxManage controlvm "dev" natpf1 "tcp-port$fancyport,tcp,,$fancyport,,$fancyport";
