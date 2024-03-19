FROM debian:latest
RUN apt-get update && \
    apt-get install -y mosquitto-clients  avahi-utils
COPY subscribe-data.sh .
RUN chmod a+x subscribe-data.sh
CMD ./subscribe-data.sh