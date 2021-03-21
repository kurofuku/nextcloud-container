# nextcloud-container
First you need to download the latest nextcloud package as latest.zip
https://download.nextcloud.com/server/releases/latest.zip

# To build image
sudo rm -rf nextcloud_data && mkdir nextcloud_data && sudo chown www-data:www-data nextcloud_data && \
sed 's/__GROUPNAME__/YOURNAME/' nextcloud-container/Dockerfile.template | sed 's/__USERNAME__/YOURGROUP/' | sed 's/__PASSWORD__/YOURPASSWORD/' | sed 's/__DOMAIN_NAME__/YOURDOMAIN/' | sed 's/__WWW_DOMAIN_NAME__/YOURWWWDOMAIN/' | sed 's/__MAIL_ADDRESS__/YOURMAIL/' | sudo docker build -t nextcloud-image -

# To run container
sudo docker run -dit -v `pwd`/nextcloud:/var/www/html/nextcloud -v `pwd`/nextcloud_data:/var/www/nextcloud_data -p 80:80 -p 443:443 -p 22:22 nextcloud-image
