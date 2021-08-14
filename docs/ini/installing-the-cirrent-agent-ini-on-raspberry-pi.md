# Installing the Cirrent Agent (INI) on Raspberry Pi

==This guide should take approximately 30 minutes to complete==

# Overview

This guide covers how to install, configure, run, and use the Cirrent Agent on your Raspberry Pi to enable the IoT Network Intelligence feature. By the end of this guide you will have the latest Cirrent Agent running on your Raspberry Pi and reporting data to the Cirrent Cloud. Data will be displayed in your Cirrent Console account.

# Requirements

-   Raspberry Pi 3B with a supported power supply
    
    -   [https://www.raspberrypi.org/products/raspberry-pi-3-model-b/](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/)
        
    -   [https://www.raspberrypi.org/documentation/hardware/raspberrypi/power/README.md](https://www.raspberrypi.org/documentation/hardware/raspberrypi/power/README.md)
        

==Other Raspberry Pis may work, but we test the agent with the Raspberry Pi 3B==

-   2.4 GHz Wi-Fi Network
    
    Raspberry Pi 3B radio only supports 2.4 GHz networks
-   Raspbian OS 2020-02-14  **Clean**  Install
    
    [https://downloads.raspberrypi.org/raspbian/images/](https://downloads.raspberrypi.org/raspbian/images/)
-   Raspberry Pi Terminal access
    
    [https://www.raspberrypi.org/documentation/usage/terminal/](https://www.raspberrypi.org/documentation/usage/terminal/)
-   A Cirrent Console account:
    
    Please register for console account using the invite email sent by Cirrent team. You can also request an account by contacting  [support@cirrent.com](mailto:support@cirrent.com)
    
-   The Cirrent Agent 1.50 Raspberry Pi .deb package - [Download](https://support.cirrent.com/hc/article_attachments/360081911994/cirrent-agent_1.50-ini_deb10u3_armhf.deb)

# Setup

1.  Make sure your Raspberry Pi is running a clean OS installation and is powered on with your official Raspberry Pi power supply
    
2.  Make sure your Raspberry P is connected to the 2.4 GHz Wi-Fi network and can reach the Internet
    
    [https://www.raspberrypi.org/documentation/configuration/wireless/](https://www.raspberrypi.org/documentation/configuration/wireless/)
3.  Make sure you have device credentials (Device ID and Secret) ready for the Cirrent Agent. Each Cirrent Agent must have its own credentials to communicate with the Cirrent Cloud. Please use device credentials as provided by Cirrent team.
    

# Installation

**1. Update your Raspberry Pi:**
```
sudo apt-get update
```
**2. Install the Cirrent Agent 1.50 .deb package and its dependencies:**
```
sudo dpkg -i cirrent-agent_1.50-ini+deb10u3_armhf.deb  
  
#############################################  
# Note: some errors may be reported by dpkg #  
#         See output below                  #  
#############################################  
  
dpkg: dependency problems prevent configuration of cirrent-agent:  
 cirrent-agent depends on monit; however:  
  Package monit is not installed.  
dpkg: error processing package cirrent-agent (--install):  
 dependency problems - leaving unconfigured  
Processing triggers for systemd (241-7~deb10u2+rpi1) ...  
Errors were encountered while processing:  
 cirrent-agent  
  
#############################################  
# You can safely ignore these ^ errors      #  
#############################################
```
```
#############################################  
# Finish installation. This will also       #  
# resolve errors from previous step         #  
#############################################  
  
sudo apt-get -f install
```
**3. Personalize your device by entering your device credentials:**
```
sudo /etc/cirrent/scripts/personalize.sh /etc/cirrent/
```
**4. Reboot your Raspberry Pi**
```
sudo reboot
```
==All done! You can now leave your Raspberry Pi running and the Cirrent Agent will automatically collect data.==

# Checking the Data

The Cirrent Agent will start reporting some data like the SSID, BSSID, router that the Raspberry Pi is connected to after the first few minutes, while some data like metrics and connectivity values take up to a day for the Cirrent Agent to collect and report.

To view data for all devices in an account, please visit:

[https://console.cirrent.com](https://console.cirrent.com/device-inspector/network-connectivity)

To start viewing your Raspberry Pi’s data simply go the Device Inspector page and search for your device:

[https://console.cirrent.com/device-inspector/network-connectivity](https://console.cirrent.com/device-inspector/network-connectivity)

-   [cirrent-agent_1.50-ini deb10u3_armhf.deb](https://support.cirrent.com/hc/en-us/article_attachments/360081911994/cirrent-agent_1.50-ini_deb10u3_armhf.deb)
    
    90 KB  [Download](https://support.cirrent.com/hc/en-us/article_attachments/360081911994/cirrent-agent_1.50-ini_deb10u3_armhf.deb)
