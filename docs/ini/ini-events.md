# INI Events

# Events:

An event is an issue or error experienced by a device. Below is a list of Events that the Cirrent Agent collects and that are analyzed in the Cirrent Cloud. When you're in your instance of the Cirrent Console, you may see some or all of these metrics affecting the devices in your fleet. You can also add  [Custom Events](ini-custom-data-api)  to monitor your application.

**Network Performance Score:** This metric shows the overall connectivity score

These metrics indicate that the device is disconnected and help you to understand what caused the disconnection:

**Wi-Fi Not Associated:** Device is not connected to the Wi-Fi network

**Wi-Fi Disassociated:**  Received disconnected or disassociated event from Wi-Fi library

**Wi-Fi Failed Association:**  Wi-Fi Association started but failed

**Gateway Error:** Device is having trouble communicating with the router

**Gateway Internet Error:** User's router is not connected to the Internet

**TLS Errors:** HTTPS request to a configured validation target fails with a TLS error, either due to certificate expired, or certificate valid in the future, or certificate hostname mismatch

**DHCP Errors:** DHCP errors due to no gateway present, or no IP address present, or no netmask present

**DNS Error/DNS Timeout:** DNS lookup to configured URL failed, but is connected to the internet

**Destination Service Unreachable:** Device is connected to internet, but unable to reach destination server

These metrics indicate atypical RF conditions:

**High PER:** High % of packets sent over Wi-fi are either failing or experiencing retries

**BSSID Switch:** BSSID of Wi-Fi router changed since last sample. Device may have an unstable Wi-Fi connection because of your mesh router or extender

**Low Signal Strength:** Device is too far from the router or there is something blocking the Wi-Fi signal to the device

**Wi-Fi Interference:** Device is experiencing Wi-Fi interference while uploading data

These metrics enable you to understand system level performance of your fleet of connected products in the field:

**High CPU Usage:** CPU usage is above a configurable threshold

**High Memory Usage:** Memory usage is above a configurable threshold

**Restarted:** The system was restarted

**Restart Triggered:**  Cirrent Agent detected something in the system triggered a restart

**Shutdown Triggered:**  Cirrent Agent detected something in the system triggered a shutdown
