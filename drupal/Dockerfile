FROM drupal:8-apache
USER root
ARG subdir_name=drupal
RUN mkdir /var/www/html/${subdir_name} && \
     ls -a /var/www/html | grep -v ${subdir_name} | tail -n+3 | xargs mv -t ${subdir_name} && \
     touch /var/www/html/.htaccess && \
     echo "RewriteRule ^$$ $subdir_name/$$1 [L]" >> /var/www/html/.htaccess && \
     echo 'RewriteCond %{REQUEST_FILENAME} !-d' >> /var/www/html/.htaccess && \
     echo 'RewriteCond %{REQUEST_FILENAME} !-f' >> /var/www/html/.htaccess && \
     echo "RewriteRule ^(.*)$$ $subdir_name/$$1 [L]" >> /var/www/html/.htaccess && \
     sed -i "/RewriteBase \/$subdir_name/s/^  #//g" /var/www/html/${subdir_name}/.htaccess