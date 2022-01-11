https://github.com/MagePsycho
https://github.com/tschifftner/

https://github.com/tschifftner/magento2-deployscripts\



oot@ip-172-31-4-4:/home/ubuntu# cat /var/www/cron/elasticsearch_autostart.sh
#!/bin/sh

STATUS="$(systemctl is-active elasticsearch)"
Result=active
if [ X"$STATUS" = X"$Result" ];
then
   echo "ElasticSearch is running"
else
   echo "ElasticSearch is not running"
   /etc/init.d/elasticsearch restart
fi

