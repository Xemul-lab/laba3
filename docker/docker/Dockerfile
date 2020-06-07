FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p Xemul-lab/img && \
    chmod -R 754 /var/www/Xemul-lab/ && \
    useradd Dima && groupadd Sergeev && usermod -aG Sergeev Dima && \
    chown -R Dima:Sergeev /var/www/Xemul-lab/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/Xemul-lab/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user Dima/g' /etc/nginx/nginx.conf
ADD index.html /var/www/Xemul-lab/
ADD img.png /var/www/Xemul-lab/img/
CMD ["nginx", "-g", "daemon off;"]