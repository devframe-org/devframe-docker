FROM devframe-centos

USER root

RUN yum -y install expat-devel \
 && yum -y install httpd-devel

RUN mkdir -p /data/tool

ADD files/apr-1.6.5.tar.gz /data/tool/
ADD files/apr-util-1.6.1.tar.gz /data/tool/
ADD files/pcre-8.42.tar.gz /data/tool/
ADD files/httpd-2.4.37.tar.gz /data/tool/
ADD files/tomcat-connectors-1.2.46-src.tar.gz /data/tool/

RUN cd /data/tool/apr-1.6.5 && ./configure --prefix=/usr/local/apr && make && make install
RUN cd /data/tool/apr-util-1.6.1 && ./configure --prefix=/usr/local/apr-util --with-apr=/usr/local/apr && make && make install
RUN cd /data/tool/pcre-8.42 && ./configure --prefix=/usr/local/pcre && make && make install
RUN cd /data/tool/httpd-2.4.37 && ./configure --prefix=/usr/local/apache --with-apr=/usr/local/apr --with-apr-util=/usr/local/apr-util --with-pcre=/usr/local/pcre --enable-so --enable-rewrite && make && make install
RUN cd /data/tool/tomcat-connectors-1.2.46-src/native && ./configure --with-apxs=/bin/apxs && make && make install

RUN cp /usr/lib64/httpd/modules/mod_jk.so /usr/local/apache/modules/
ADD conf/httpd.conf /usr/local/apache/conf/
ADD conf/workers.properties /usr/local/apache/conf/

EXPOSE 80 443

CMD ["/usr/local/apache/bin/apachectl", "-DFOREGROUND"]