# MagicMirrorIoTEdge

My attempt at putting magicmirror on the IOT Edge and learn on a rock-3a

image: https://github.com/radxa-build/rock-3a/releases/download/main-a7204124/rock-3a-ubuntu-focal-server-arm64-20220501-0200-gpt.img.xz

doc: https://wiki.radxa.com/Rock3/Debian

1. portal.azure.com
    - Create IOT Hub (rpi4iothub)
    - Create Iot Edge Device (rk3adevice)


Start Raspberry Pi Imager
download https://github.com/radxa-build/rock-3a/releases/download/main-a7204124/rock-3a-ubuntu-focal-server-arm64-20220501-0200-gpt.img.xz
select and write rock-3a-ubuntu-focal-server-arm64-20220501-0200-gpt.img.xz

install sd in rock-3a
ssh rock@rock-3a.mcp 


$ sudo apt-get update

$ sudo apt-get install -y rockchip-overlay

$ sudo apt-get install -y linux-4.19-rock-3-latest

config using the /boot/uEnv.txt

1. NO Wifi? : only if you buy the adapter!!!

Install IOT Edge https://docs.microsoft.com/en-us/azure/iot-edge/how-to-provision-single-device-linux-symmetric?view=iotedge-2020-11&tabs=visual-studio-code%2Crpios for Ubuntu 20.04

sudo apt install wget
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb
sudo apt-get update; \
  sudo apt-get install moby-engine
  
sudo nano /etc/docker/daemon.json
 - {
      "log-driver": "local",
      "dns": ["ip.of.my.localRouter"]
   }
   - sudo systemctl restart docker

sudo nano /etc/sysctl.conf
    - uncomment line below
net.ipv4.ip_forward=1
sudo systemctl restart docker
   
 sudo apt-get update; \
  sudo apt-get install aziot-edge defender-iot-micro-agent-edge
  
sudo iotedge config mp --connection-string 'PASTE_DEVICE_CONNECTION_STRING_HERE'
sudo iotedge config apply
sudo iotedge check


When you create a new IoT Edge device, it will display the status code 417 -- The device's deployment configuration is not set in the Azure portal. This status is normal, and means that the device is ready to receive a module deployment.
