FROM devframe-centos

USER root

RUN mkdir -p /data/tool

ADD files/apr-1.6.5.tar.gz /data/tool/
ADD files/apr-util-1.6.1.tar.gz /data/tool/
ADD files/pcre-8.42.tar.gz /data/tool/
ADD files/httpd-2.4.37.tar.gz /data/tool/

RUN cd /data/tool/apr-1.6.5 && ./configure --prefix=/usr/local/apr && make && make install
RUN cd /data/tool/apr-util-1.6.1 && ./configure --prefix=/usr/local/apr-util --with-apr=/usr/local/apr && make && make install
RUN cd /data/tool/pcre-8.42 && ./configure --prefix=/usr/local/pcre && make && make install
RUN cd /data/tool/httpd-2.4.37 && ./configure --prefix=/usr/local/apache --with-apr=/usr/local/apr --with-apr-util=/usr/local/apr-util --with-pcre=/usr/local/pcre --enable-so --enable-rewrite && make && make install

ADD startup.sh /usr/local/apache/bin/

RUN chmod 755 /usr/local/apache/bin/startup.sh

EXPOSE 80 443

CMD ["/usr/local/apache/bin/apachectl", "-DFOREGROUND"]