# Testing the CA for IoT Network Intelligence (INI)

# Testing

For testing you'll need a device with the CA installed and configured to run INI.

To start testing, power up your device and connect it to the internet.

You can log in to the Cirrent console, go to Device Inspector / Attributes to check the attributes (eg: router, city), and State (eg: SSID, BSSID)

Let the device run for a day to populate some INI event data in the cloud. After a day, log in to the Cirrent Console and go to the Device Inspector. Enter the device id, and you should be able to see the data coming back from the device.

## Test cases

Here is a summary of some of the use cases that you can test to make sure the INI functionality for the CA is working correctly. The metrics will show in the console a day later.

1.  Generate a ‘Low Signal Strength’ events by keeping device far from the router or dropping the WiFI router signal strength (e.g. removing the router antennas, shielding the device)
2.  Generate a ‘Gateway Error’ events by unplugging the power from the router.
3.  Generate a ‘Gateway Internet Error’ events by unplugging the Ethernet backhaul cable from the WiFi router.

If you have any trouble or questions, reach out to us:  [support@cirrent.com](mailto:support@cirrent.com)
