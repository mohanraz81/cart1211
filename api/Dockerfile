#Docker file cart API layer
FROM centos:7
MAINTAINER mohanraz@gmail.com
RUN yum -y update
ADD scripts /opt
RUN chmod 755 /opt/*.sh
RUN /opt/installpackages.sh
ADD config /opt
RUN cp /opt/httpd.conf /etc/httpd/conf/httpd.conf
RUN mkdir -p /apps/cart/html
ADD code /apps/cart/html
RUN ln -sf  /proc/self/fd/2 /var/log/httpd/error_log && ln -sf  /proc/self/fd/1 /var/log/httpd/access_log
ENV BACKENDLB=backend
EXPOSE 80
CMD ["/opt/startapache.sh"]