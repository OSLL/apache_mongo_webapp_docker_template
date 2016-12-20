FROM tknerr/baseimage-ubuntu:14.04
RUN apt-get update && apt-get -y install vim nano
RUN apt-get -y install mongodb python-pip python-dev git apache2 libapache2-mod-wsgi
RUN pip install pymongo==3.4
RUN pip install mongoengine
RUN rm /etc/apache2/sites-enabled/000-default.conf /etc/apache2/sites-available/000-default.conf
RUN mkdir -p /data/db
RUN chown -R mongodb:mongodb /data
RUN sed -i 's/journal=true/journal=false/g' /etc/mongodb.conf
