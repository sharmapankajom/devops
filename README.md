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
##############################################################################################################################################



php bin/magento maintenance:enable                                                                                                        
rm -rf pub/static/* var/cache/* var/view_preprocessed/* generated/*                                     
php bin/magento setup:upgrade                                                                           
php bin/magento setup:di:compile                                                                        
php bin/magento setup:static-content:deploy -j 6 -f               
php bin/magento indexer:reindex
php bin/magento cache:flush                                                                             
php bin/magento cache:clean
php bin/magento maintenance:disable
#####################################################################################################
