FROM debian:jessie

# Thanks Victor Seva for dockerfile script
MAINTAINER Konstantin Tumalevich <userad@gmail.com>

# Important! Update this no-op ENV variable when this Dockerfile
# is updated with the current date. It will force refresh of all
# of the base images and things like 'apt-get update' won't be using
# old cached versions when the Dockerfile is built.
ENV REFRESHED_AT 2018-02-08

# avoid httpredir errors
RUN sed -i 's/httpredir/deb/g' /etc/apt/sources.list

RUN rm -rf /var/lib/apt/lists/* && apt-get update &&   apt-get install --assume-yes gnupg wget
# kamailio repo
RUN echo "deb http://deb.kamailio.org/kamailio43 jessie main" >   /etc/apt/sources.list.d/kamailio.list
RUN wget -O- http://deb.kamailio.org/kamailiodebkey.gpg | apt-key add -

RUN apt-get update && apt-get install --assume-yes kamailio kamailio-autheph-modules kamailio-carrierroute-modules kamailio-cnxcc-modules kamailio-cpl-modules kamailio-dbg kamailio-dnssec-modules kamailio-erlang-modules kamailio-extra-modules kamailio-geoip-modules kamailio-ims-modules kamailio-java-modules kamailio-json-modules kamailio-kazoo-modules kamailio-ldap-modules kamailio-lua-modules kamailio-memcached-modules kamailio-mono-modules kamailio-mysql-modules kamailio-nth kamailio-outbound-modules kamailio-perl-modules kamailio-postgres-modules kamailio-presence-modules kamailio-purple-modules kamailio-python-modules kamailio-radius-modules kamailio-redis-modules kamailio-sctp-modules kamailio-snmpstats-modules kamailio-sqlite-modules kamailio-tls-modules kamailio-unixodbc-modules kamailio-utils-modules kamailio-websocket-modules kamailio-xml-modules kamailio-xmpp-modules

VOLUME /etc/kamailio

# clean
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

CMD ["kamailio", "-DD", "-E"]
