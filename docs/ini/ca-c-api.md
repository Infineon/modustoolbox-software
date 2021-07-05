# CA C API

## CA API

Cirrent's CA API gives your device code the ability to:

1.  Initialize the API
2.  Check on the status and capabilities of the currently connected network
3.  Retrieve a list of private networks configured for this device
4.  Add or delete private networks from this device
5.  Get the Wi-Fi scan list
6.  Get device info
7.  Set device location
8.  Set user action (tell Cirrent cloud that user took an action on the device)
9.  Upload product data to the Cirrent cloud
10.  Reset the device status in the Cirrent cloud
11.  Wake or sleep the CA
12.  Start WPS
13.  Make device discoverable (turn on SoftAP, tell Cirrent cloud to make discoverable)
14.  Revert to last known good CA configuration
15.  Get notified when there is a change in the connectivity status.
16.  Get notified when the device should perform its identifying action (e.g. play a sound, turn on a light)
17.  Get notified when the device should perform some product-specific action

Note that the CA must be running for the API methods to be executed.

The API provides programmatic interfaces to do this directly from your code with the following commands:

**Init**

**Command:** _cac_init_

**Description:** When the API is no longer needed, this method should be  called to disable all notifications and free the API internals.

**Inputs: Initializes the API. Must be called before any other API calls are made.**

-   **stack-size:** the size of the stack. The function takes a stack size as an argument and creates a worker thread with the given stack size. The status/action callbacks will be called from the worker thread context.

**Outputs:** none

**Returns:** returns 0 on success, a non-zero error code on failure

**Cleanup**

**Command:** _cac_cleanup_

**Description:**When the API is no longer needed, this method should be  called to disable all notifications and free the API internals.

**Inputs:** none

**Outputs:** none

**Returns:** returns 0 on success, a non-zero error code on failure

**Get Network Status**

**Command:** _cac_get_network_status_

**Description:** Retrieves the current network status and the network capabilities. Your device code should use this information to determine which services can be started on the device. For example, with a 20kbps bandwidth limitation you will not want to start video streaming.

**Inputs:** none

**Outputs:**

-   **Connection Status:** Connected, Disconnected, Ready-for-onboarding, onboarding-disabled, Failed-to-join-private-network
-   **Network Type:** Specifies whether the network is a ZipKey network or a private network
-   **Network Security:** the security type of the network (none, WPA, WPA2-Enterprise, WISPr)
-   **Domains:** what domains are reachable by the device on this network (none, any, or a semicolon-delimited list of domains)
-   **Priority:** The priority that was assigned to this network
-   **Bandwidth:** bandwidth limit for this network, or 0 if unlimited If the device is connected to a private network it also passes back
-   **SSID:** the SSID of the connected network as printable ASCII string
-   **HEX_SSID:**  SSID as hexdump string
-   **BSSID:** the BSSID of the router the devices is connected to
-   **Roaming Id:** If a Hotspot 2.0 network, the hotspot 2.0 roaming consortium id of the connected network
-   **Credential Id:** The credential id that was used to define this network

**Returns:** returns 0 on success, a non-zero error code on failure

Note that when the device is in “ready for onboarding state”, then connection_status is READY_FOR_ONBOARDING at each call. A user can obtain connection information from other CAC_NETWORK_STATUS_T fields for information about what type of network (if any) the CA is on.

**Get Private Networks**

**Command:** _cac_get_private_networks_

**Description:** Retrieves a null-terminated list of user-configured networks for this device.

**Inputs:** none

**Outputs:** List of user networks, each of which contains

-   **Source:** where the user network was configured. This can be either "Cirrent" if the network was configured via the Cirrent cloud, or "Device" if the credentials were passed to the CA with the cac_add_private_network function, or "SoftAP" if the credentials were passed through the SoftAP process
-   **SSID:** the SSID of the network
-   **HEX_SSID:**  SSID as hexdump string
-   **Roaming Id:** The hotspot 2.0 roaming consortium id of the connected network (if a Hotspot 2.0 network)
-   **Security:** The security type of the network (none, WPA, WPA2-Enterprise, WISPr)
-   **Priority:** The priority that was assigned to this network
-   **Credential Id:** The credential id that was used to define this network
-   **Status:** status of the network (unused, joining, joined, failed, not_found, disconnected, confirmed)
-   **Disconnect reason:**  reason of last disconnection (disconnect_request, connection_lost, not_found, assiciation error, incorrect_password, dhcp_timeout, internet_not_reachable, rsa_decryption_error)

**Returns:** returns 0 on success, a non-zero error code on failure

_cac_free_private_networks_  should be called to free the list of networks that was returned by  _cac_get_private_networks_.

**Add Private Network**

**Command:** _cac_add_private_network_

**Description:** Adds a private network for this device.

**Inputs:**

-   **SSID:** the SSID of the network to add.
-   **Roaming Id:** the Hotspot 2.0 roaming consortium id (if a Hotspot 2.0 network)
-   **Security:** the type of security for this network (none, WPA, WPA2-Enterprise, WISPr)
-   **Hidden:** Whether the SSID is hidden or broadcast
-   **Pre-Shared Key:** If a WPA network, the pre-shared key to use to authenticate
-   **Username:** If a WPA2-Enterprise or WISPr network, the username to use to authenticate
-   **Password:** If a WPA2-Enterprise or WISPr network, the password to use to authenticate
-   **Priority:** The priority to assign to this network. Priorities are in the range of 0-255, with ZipKey networks in the range of 1-150, and private networks in the range of 150-250. Higher priority networks will be chosen before lower priority networks.
-   **Certificate validation:** If the CA should validate the server certificate for this network, this is the expected server certificate.
-   **Credential id:** A unique id for this credential (a string, used for report status).

**Outputs:** none

**Returns:** returns 0 on success, a non-zero error code on failure

**Delete Private Network**

**Command:** _cac_delete_private_network_

**Description:** Deletes a private network for this device by matching the SSID or HEX_SSID or Roaming Consortium Id.

**Inputs:**

-   **SSID:** the SSID of the network to delete
-   **HEX_SSID:**  SSID as hexdump string
-   **Roaming Id:** For Hotspot 2.0 network, the Hotspot 2.0 roaming consortium id for the network to delete

**Outputs:** none

**Returns:** returns 0 on success, a non-zero error code on failure

**Set Location**

**Command:** _cac_set_location_

**Description:** Sets the location (GPS coordinates) for this device.

**Inputs:**

-   **Latitude:** the current device latitude
-   **Longitude:** the current device longitude
-   **Accuracy:** the accuracy of the measurement in meters.

**Outputs:** none

**Returns:** returns 0 on success, a non-zero error code on failure

**Get WiFi Scan**

**Command**: _cac_get_wifi_scan_

**Description**: Retrieves the most recent Wi-Fi scan. Typically the CA takes care of the WiFi connection so the device should not need visibility to the Wi-Fi scan. This is in case the device supports some alternative local onboarding (e.g. via BLE) and needs access to the Wi-Fi scan list.

**Inputs**: none

**Outputs**: A list of networks, each of which contains -

-   **SSID**: the SSID of the network
-   **HEX_SSID:**  SSID as hexdump string
-   **BSSID**: the BSSID of the network
-   **Roaming Id**: If a Hotspot 2.0 network, the hotspot 2.0 roaming consortium id of the network
-   **Security:** the type of security for the network (none, WPA, WPA2-Enterprise, WISPr)
-   **Flags**: The flags, as returned by the wpa_supplicant - e.g. [WPA2-PSK-CCMP][ESS]
-   **Signal level**: The signal level for this network
-   **Frequency**: The frequency in MHz (e.g. 2412 = channel 1)

**Returns**: returns 0 on success, a non-zero error code on failure

_cac_free_wifi_scan_  should be called to free the network list that was returned by  _cac_get_wifi_scan_.

**Get Device Info**

**Command**: _cac_get_device_info_

**Description**: Retrieves identifying info about this device, in case it is needed for some alternative on boarding process.

**Inputs**: none

**Outputs**:

-   **Device id**: The unique identifier for this device
-   **DUB key**: The Product User Binding key (an additional key to differentiate the device)
-   **SCD key**: Public key used to encrypt private network credentials

**Returns**: returns 0 on success, a non-zero error code on failure

**Set User Action**

**Command**: _cac_set_user_action_

**Description**: Tells the CA that the user has taken some action on the device. This can be used as an extra precaution during the on boarding process to confirm that the user is on boarding the correct device. The CA will send a status update to the Cirrent cloud so that the app knows that the user took an action.

**Inputs**:

-   **Action name**: the name of the action the user took (in case there is more than one possible user action).

**Outputs**: none

**Returns**: returns 0 on success, a non-zero error code on failure

**Revert CA**

**Command:** _cac_revert_

**Description:** Revert the CA configuration to the last known good configuration.

**Inputs:** none

**Outputs:** none

**Returns:** returns 0 on success, a non-zero error code on failure

**Reset Device**

**Command**: _cac_reset_device_

**Description**: Clears the device settings and history from the Cirrent cloud.

**Inputs**: none

**Outputs**: none

**Returns**: returns 0 on success, a non-zero error code on failure

**Upload Data**

**Command:** _cac_upload_data_

**Description:** Upload data to Cirrent's cloud

**Inputs:**

-   **key:** an identifier for this data
-   _*value:_ the data to upload

**Outputs:** none

**Returns:** returns 0 on success, a non-zero error code on failure

**Wake CA**

**Command:** _cac_wake_

**Description:** Triggers the CA to start normal operation (looking for networks, checking for private wi-fi credentials, updating network configuration, uploading log files etc.)

**Inputs:** none

**Outputs:** none

**Returns:** returns 0 on success, a non-zero error code on failure

**Sleep CA**

**Command:** _cac_sleep_

**Description:** Triggers the CA to stop actively managing the connection, or interacting with the Cirrent cloud. This can be done to conserve power, as the CA moves into a dormant mode, where it only responds to a command from the API to start.

**Inputs:** none

**Outputs:** none

**Returns:** returns 0 on success, a non-zero error code on failure

**Start WPS**

**Command**: _cac_start_wps_

**Description**: Triggers the CA to start WPS (Wi-Fi Protected Setup) protocol between the device and the router.

**Inputs**: none

**Outputs**: none

**Returns**: returns 0 on success, a non-zero error code on failure

**Make Device Discoverable**

**Command**: _cac_make_discoverable_

**Description**: Triggers the CA to bring up the SoftAP so that the user has the option to locally configure the private network credentials. When the device is first powered up, and has no private networks, the CA will take care of starting/stopping SoftAP. This call is for the case where the user wants to re-provision their device, and has pressed a button to put the device back into on-boarding mode. If the CA is connected to the Cirrent cloud, it will also tell the cloud to make the device discoverable (no longer consider it bound to a user account).

**Inputs**: none

**Outputs**: none

**Returns**: returns 0 on success, a non-zero error code on failure

**Getting notified on connection status changes**

**Command**: _cac_register_network_status_handler_

**Description**: For both Linux and Embedded implementations, Cirrent also provides a way to register a callback function so your code receives a notification when the network connection status changes. This makes it unnecessary to run a timer and periodically check the network status. In many devices, this will replace any hooks you have to wpa_supplicant, dhclient, or the underlying radio drivers. You register a callback via the function cac_register_network_status_handler. Your cac_network_status_handler will be called whenever the network status changes. Your application can then call cac_get_network_status to get detailed information about the connection.

Your callback will be called once with READY_FOR_ONBOARDING connection_status when the device enters “ready for onboarding” state. When the device exits “ready for onboarding” status, then it calls the callback with ONBOARDING_DISABLED connection_status.

Your callback will get called with CONNECTED when the device joins a network. You can then call cac_get_network_status to determine if it was a ZipKey or a private network. Your callback will get called with DISCONNECTED when the device falls off a network. Your callback will get called with FAILED_TO_JOIN_PRIVATE_NETWORK connection_status whenever the device fails its attempt to join a private network.

**Inputs**: handler to be called when network status changes

**Outputs**: none

**Returns**: returns 0 on success, a non-zero error code on failure

**Getting notified on action changes**

**Command**: _cac_register_action_handler_

**Description**:Some products will have an option for the user to get some confirmation that the right device is being onboarded (e.g. a light flashes or a sound plays). To implement this, you register a callback function so your code receives a notification that the action is to be performed. You register a callback via the function cac_register_action_handler. Your cac_action_handler will be called whenever the app requests that the identifying action occur.

**Inputs**: handler to be called when network status changes

**Outputs**: none

**Returns**: returns 0 on success, a non-zero error code on failure

**Enable notifications**

**Command**: _cac_enable_notifications_

**Description**: Enable all notifications (network status updates, action handlers) from ca_agent.

**Inputs**: none

**Outputs**: none

**Returns**: returns 0 on success, a non-zero error code on failure

**Disable notifications**

**Command**: _cac_disable_notifications_

**Description**: Disable all notifications (network status updates, action handlers) from ca_agent.

**Inputs**: none

**Outputs**: none

**Returns**: returns 0 on success, a non-zero error code on failure

**Get version of CA**

**Command**: _cac_get_ca_version_

**Description**: Get the version of the CA.

**Inputs**: none

**Outputs**: none

**Returns**: returns 0 on success, a non-zero error code on failure
