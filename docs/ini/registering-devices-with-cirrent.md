# Registering Devices with Cirrent

This article applies to both Zipkey and IoT Network Intelligence (INI) products.

Before devices are ready to be used in the field, they must be registered with the Cirrent service, and be provisioned with credentials to connect to the Cirrent service. Those credentials should be stored within the device during the manufacturing process.

### Prerequisites:

You will need an account on  [Cirrent console](https://console.cirrent.com/login)

==**Note:**  You can use either Method 1 or Method 2 described below to register your devices.==

### Method 1: Using Cirrent Console

Step 1: Define your [Device Type](device-provisioning-security-options)  in the  [Manage Device Types page](https://go.cirrent.com/management/device-type).

Step 2: Define Device Credentials are in the form of Device ID and Secret as described [here](https://support.cirrent.com/hc/en-us/articles/217518466).

Step 3: There are two ways to register your devices using Console:

a. During prototyping phase, you can register Devices individually  [here](https://console.cirrent.com/devices)

b. During manufacturing phase, you can bulk upload a set of devices using the "Bulk Upload" link on the top right corner of this  [page](https://console.cirrent.com/devices). The format for the bulk upload file is a CSV file of device IDs and device secrets (newlines are ignored):
```
device1, secretfordevice1, device2, secretfordevice2, device3, secretfordevice3,  
  
device4, secretfordevice4, device5, secretfordevice5
```
### Method 2: Using Cirrent Operations API

You can also register devices by using [Operations API](https://app.swaggerhub.com/apis/Cirrent/api-ops/1.0.0-oas3#/) during manufacturing process to programmatically register your devices.

Step 1: Define  [Device Type](device-provisioning-security-options)  using POST /devicetypes and passing JSON payload as shown in [Operations API](https://app.swaggerhub.com/apis/Cirrent/api-ops/1.0.0-oas3#/)

Step 2: Define Device Credentials are in the form of Device ID and Secret as described [here](device-provisioning-security-options).

==**Note:**  You can try out the different  [Operations API](https://app.swaggerhub.com/apis/Cirrent/api-ops/1.0.0-oas3#/)  calls shown in next few steps by clicking "Authorize" on the top right of the  [Operations API page](https://app.swaggerhub.com/apis/Cirrent/api-ops/1.0.0-oas3#/).  [More details on Ops API are here](using-ops-api-to-register-devices). Click "Tryout" to edit the different JSON payloads and see the results.==

Step 3: Get Device Type ID using GET /devicetypes

Step 4: Register a set of Devices using PUT /devicetypes/{device_type_id}/device_ids and passing JSON payload as shown in [Operations API](https://app.swaggerhub.com/apis/Cirrent/api-ops/1.0.0-oas3#/)

Step 4: Check the results showing new devices in the  [Cirrent Console](https://console.cirrent.com/devices)

==**Note:**  If you don't see your newly registered devices in the Console, please check the filter on the right top corner of the page to confirm if you have the correct Device Type chosen.==
