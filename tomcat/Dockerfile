FROM devframe-centos

USER root

RUN mkdir /data
RUN chmod 775 data

RUN useradd -u 185 -G root webwas

ADD files/jdk-8u191-linux-x64.tar.gz /usr/local/

ENV JAVA_HOME /usr/local/jdk1.8.0_191

ADD files/apache-tomcat-8.5.35.tar.gz /usr/local/

ARG TOMCAT_PATH=/usr/local/apache-tomcat-8.5.35

RUN chmod +x ${TOMCAT_PATH}/bin/*.sh \
  && chown -R webwas:root ${TOMCAT_PATH}

ENV CATALINA_HOME ${TOMCAT_PATH}
ENV PATH $JAVA_HOME/bin:$CATALINA_HOME/bin:$PATH

EXPOSE 8080

USER webwas

CMD ["catalina.sh", "run"]