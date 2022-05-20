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

$ nmcli dev wifi connect "wifi_name" password "wifi_password"
