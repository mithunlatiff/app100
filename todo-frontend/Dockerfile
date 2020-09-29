FROM registry.access.redhat.com/ubi8:8.0

LABEL version="1.0" \
 description="To Do List application front-end" \
 creationDate="2017-12-25" \
 updatedDate="2019-08-01" 

LABEL io.k8s.description="This is a sample APP" \
 io.openshift.expose-services="80:http" \
 io.openshift.tags="apache, httpd" \
 io.k8s.display-name="test image" 

ENV BACKEND_HOST=localhost:8081 \
  DIR=/run/nginx.pid \
  DIRR=/var/log/nginx \
  DI=/etc/nginx/ \
  MM=nginx.conf

RUN yum install -y --disableplugin=subscription-manager --nodocs nginx nginx-mod-http-perl && \
 yum clean all

COPY ${MM} ${DI}

RUN touch ${DIR} && \
 chgrp -R 0 ${DIRR} ${DIR} && \
 chmod -R g+rwx ${DIRR} ${DIR} 
  
COPY src/ /usr/share/nginx/html

EXPOSE 8080

USER root

CMD nginx -g "daemon off;"

