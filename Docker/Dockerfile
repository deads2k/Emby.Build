# Emby Server
# Contributors: gfjardim <gfjardim@gmail.com>
FROM phusion/baseimage:0.9.16
MAINTAINER Carlos Hernandez <carlos@techbyte.ca>

#########################################
##        ENVIRONMENTAL CONFIG         ##
#########################################
# Set correct environment variables
ENV HOME="/root" LC_ALL="C.UTF-8" LANG="en_US.UTF-8" LANGUAGE="en_US.UTF-8"

# Valid value are true or false. If set to true, the container will attempt to update at 3am every morning.
# Setting this to true will break container orchestration platforms like Kubernetes or OpenShift
ENV AUTO_UPDATES_ON=false

# TimeZone. (i.e America/Edmonton)
ENV TZ=America/Edmonton

# User ID emby should run under, default is 99 for unRAID compatiability.
ENV MB_USER_ID=99

# Group ID emby should run under, default is 100 for unRAID compatiability.
ENV MB_GROUP_ID=100

# Use baseimage-docker's init system
CMD ["/sbin/my_init"]


#########################################
##         RUN INSTALL SCRIPT          ##
#########################################
COPY ./install.sh /tmp/
RUN chmod +x /tmp/install.sh && /tmp/install.sh && rm /tmp/install.sh


#########################################
##         EXPORTS AND VOLUMES         ##
#########################################

# Configuration files and state of MediaBrowser Server folder. (i.e. /opt/appdata/emby or /mnt/cache/.appdata/emby)
VOLUME /config 

# Location of your media
VOLUME /media 

EXPOSE 8096 8920 7359/udp 1900/udp

# User ID emby should run under, default is 99 for unRAID compatiability.
USER 99
