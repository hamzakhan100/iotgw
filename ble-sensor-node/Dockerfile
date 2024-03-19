# Use a base image
FROM debian:latest 


RUN apt-get update && \
apt-get install -y \
#BLE support (bluez)
bluez \
python3 \
#python3 support (including pydbus support)
python3-pydbus \
procps \
python3-paho-mqtt \
mosquitto-clients  \
avahi-utils

RUN useradd -m bluezuser \
    && passwd -d bluezuser

# Copy Python script into the container
COPY ./ble.py /usr/local/bin/ble.py 
RUN  chown bluezuser:bluezuser /usr/local/bin/ble.py \
     && chmod a+x /usr/local/bin/ble.py


USER bluezuser

WORKDIR /usr/local/bin/

CMD ["bash", "-c", "bluetoothctl --timeout=2 scan on && sleep 5 && python3 -u ble.py"]

# CMD ["bash", "-c", "bluetoothctl --timeout=2 scan on; sleep 5; & python3 ble.py"]


# CMD ["bash", "-c", "timeout 2s bash -c 'while true; do bluetoothctl scan le; sleep 3; done' & python3 ble.py"]





