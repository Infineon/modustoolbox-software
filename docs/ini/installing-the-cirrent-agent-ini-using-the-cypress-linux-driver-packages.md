# Installing the Cirrent Agent (INI) using the Cypress Linux Driver Packages

==This guide should take approximately 1 hour to complete==

# Overview

This guide covers how to install, configure, run, and use the Cirrent Agent on your A-Class device to enable the IoT Network Intelligence feature. By the end of this guide you will have the latest Cirrent Agent running on your device and reporting data to the Cirrent Cloud. Data will be displayed in your Cirrent Console account.

# Requirements

-   A-Class device with compatible architecture (armhf). Here is a link to the platform we use to test:
    
    -   Example device ([https://www.mouser.com/ProductDetail/NXP-Semiconductors/MCIMX6SX-SDB?qs=l5F7KFZg3O5RU%2FYaPLi77g%3D%3D](https://www.mouser.com/ProductDetail/NXP-Semiconductors/MCIMX6SX-SDB?qs=l5F7KFZg3O5RU%2FYaPLi77g%3D%3D))
        
    -   Example Wi-Fi adapter ([https://www.mouser.com/ProductDetail/Murata-Electronics/LBEH5HMZPC-TEMP-DS-SD?qs=Eq3eGuHnqhkVjHX6jas6Kg%3D%3D](https://www.mouser.com/ProductDetail/Murata-Electronics/LBEH5HMZPC-TEMP-DS-SD?qs=Eq3eGuHnqhkVjHX6jas6Kg%3D%3D))
        

==Other A-Class devices will work, but we test the agent with the linked imx6 device and Wi-Fi adapter==

-   2.4 GHz or 5GHz Wi-Fi Network (Depends on the Wi-Fi adapter you are using)
    
-   Root shell access
-   A Cirrent Console account:
    
    Please register for console account using the invite email sent by Cirrent team. You can also request an account by contacting  [support@cirrent.com](mailto:support@cirrent.com)
    
-   The Cirrent Agent 1.50 required files
    -   If you are using the example device and Wi-Fi adapter linked above, we recommend downloading the ready to use SD card image available here: ([https://community.cypress.com/docs/DOC-20046](https://community.cypress.com/docs/DOC-20046)). If you have this combo, download the linked SD card image and flash it to an SD card. It includes all the necessary files to run the Cirrent Agent.
    -   If you are using another armhf device, please download the Cirrent Agent package (cypress-cirrent-1.50.tar.gz) included in the FMAC tarball: ([https://community.cypress.com/docs/DOC-20044](https://community.cypress.com/docs/DOC-20044))
-   Required libraries included in the FMAC package in  _cypress-cirrent/usr/lib/cirrent/_  (These are already included in the Yocto SD card image):
    -   libssl 1.0.2
    -   libcrypto 1.0.2
    -   libcurl 4.5.0

# Setup

1.  Make sure your device is powered on and is connected to a Wi-Fi network that can reach the Internet. If you are using the Yocto SD card image, you can connect to Wi-Fi by following these steps:

```
mkdir /etc/wpa_supplicant  
wpa_passphrase SSID PSK > /etc/wpa_supplicant/wpa_supplicant-wlan0.conf  
systemctl enable wpa_supplicant@wlan0  
systemctl enable wpa_supplicant@wlan0  
  
echo "[Match]  
Name=wlan0  
[Network]  
DHCP=ipv4  
" > /etc/systemd/network/25-wlan0.network  
systemctl enable systemd-networkd
```
2. Generate a new provisioning key and secret in your Cirrent Console account and keep it handy. You'll need it for the installation step. You can find  [instructions on how to generate the key and secret here](https://support.cirrent.com/hc/en-us/articles/115000084846).

3. Create a new Device Type use an existing device type and make note of its ID. You can find the device type ID in the  [Device Types section of the Cirrent Console](https://console.cirrent.com/device-types).

# Installation

**1**. If you are using the Yocto SD card image you can go to step 2. If you are installing for another armhf device, please follow the instructions included in the root directory of the FMAC tarball under the "Instructions - Cirrent Agent" section of the README.

**2.** Add your provisioning key and secret. The Cirrent Agent requires these credentials to be able to communicate with the Cirrent Cloud.
```
mkdir /etc/cirrent/keys  
systemctl enable cirrent  
vi /etc/default/cirrent  

# uncomment last 2 lines and replace ACCOUNT_ID, DEVICE_TYPE_ID,   
# PROVISIONING_KEY, and PROVISIONING_SECRET with the appropriate values
```

**3.** Reboot your device
```
reboot
```
All done! You can now leave your device running and the Cirrent Agent will automatically collect data.

# Checking the Data

The Cirrent Agent will start reporting some data like the SSID, BSSID, router that the device is connected to after the first few minutes, while some data like metrics and connectivity values take up to a day for the Cirrent Agent to collect and report.

To view data for all devices in an account, please visit:

[https://console.cirrent.com](https://console.cirrent.com/device-inspector/network-connectivity)

To start viewing your device’s data simply go the Device Inspector page and search for your device:

[https://console.cirrent.com/device-inspector/network-connectivity](https://console.cirrent.com/device-inspector/network-connectivity)
