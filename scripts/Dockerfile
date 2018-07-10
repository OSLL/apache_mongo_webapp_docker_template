FROM tknerr/baseimage-ubuntu:14.04
RUN apt-get update && apt-get install -y apt-transport-https vim nano
RUN apt-get -y install 
RUN rm /etc/apache2/sites-enabled/000-default.conf /etc/apache2/sites-available/000-default.conf
RUN mkdir -p /data/db
RUN chown -R mongodb:mongodb /data
RUN sed -i 's/journal=true/journal=false/g' /etc/mongodb.conf
RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/*
ADD ./ /test
WORKDIR /test
RUN cp config/<config>.conf config/000-default.conf
ENV LC_ALL en_US.UTF-8
ENV PYTHONIOENCODING=utf-8
CMD /etc/init.d/apache2 restart && /etc/init.d/mongodb restart && ./scripts/local_deploy.sh -c survey.moevm.info -s $SEM -t $TEACHERS_FILE && /usr/sbin/sshd -D \
    -o UseDNS=no\
    -o UsePAM=no\
    -o PasswordAuthentication=yes\
    -o UsePrivilegeSeparation=no\
    -o PidFile=/tmp/sshd.pid
