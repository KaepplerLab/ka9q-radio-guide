# ka9q-radio-guide

This README will walk through the commands to reliably install ka9q-radio for use in the lab. I operate under the assumption that the user has a RPi 4B with an RX888 sdr. Since the setup process and fixes are hard to follow this should work as of 05/2025.

## Set up RPi

Start by installing Debian Bookworm 64bit with a desktop environment on an SD card or separate SSD/NVMe. Boot the RPi, open terminal, install these dependencies:

'''
sudo apt install avahi-utils build-essential make gcc libairspy-dev libairspyhf-dev libavahi-client-dev libbsd-dev libfftw3-dev libhackrf-dev libiniparser-dev libncurses5-dev libopus-dev librtlsdr-dev libusb-1.0-0-dev libusb-dev portaudio19-dev libasound2-dev uuid-dev rsync libogg-dev libsamplerate-dev libliquid-dev libncursesw5-dev libhackrf-dev
'''

## KA9Q-radio source install

'''
git clone https://github.com/ka9q/ka9q-radio.git
cd ka9q-radio
/bin/sh RPi-compile.sh
sudo make install
sudo ldconfig
'''

## Permissions

'''
sudo adduser $USER radio
sudo chown $USER /var/lib/ka9q-radio
sudo chown $USER /etc/radio
sudo chown $USER /etc/fftw
chmod -R 777 /etc/fftw
chmod -R 777 /etc/radio
sudo chmod -R 777 /var/lib/ka9q-radio
sudo chmod -R 777 /etc/avahi
'''

## Config files

Copy config file from github directory to /etc/radio and edit for use.
'''
cp ~/ka9q-radio/config/radiod@rx888-generic.conf /etc/radio
'''
