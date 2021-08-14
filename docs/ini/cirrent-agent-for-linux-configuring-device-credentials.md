# Cirrent Agent for Linux: Configuring Device Credentials

## Manually configuring device credential

Cirrent provides a script to configure the Cirrent Agent on each device. Before you start, make sure the Cirrent Agent is properly installed on the device. You'll need to have a few pieces of information available before you start:

-   **Account ID.** This is your Cirrent account ID, an integer like 1312, which you can find [here](https://go.cirrent.com/account). It lets Cirrent associate the device with a company account.
-   **Device ID.** This is the unique ID for the device.
-   **Device secret.** This is the secret that you allocated to the device, or Cirrent issued for the device. If you don't have a secret yet, make sure to register the device in the [Management Center](https://go.cirrent.com/management/devices). Make sure to double check capital I and l and 0 and O to get the secret right. You can find more information about the Device ID and secret [here](device-provisioning-security-options).

Now you can configure the device by running the personalization script:
```
# cd /etc/cirrent/scripts
```
```
# sudo ./personalize.sh /etc/cirrent
```
Now enter the information as the script asks you to.

The script will generate a credentials.key file in the /etc/cirrent/keys directory for the Cirrent Agent to use. If you do not see this file, try running the script using sudo. The script will also download list of ZipKey networks and CA certificates from the Cirrent cloud.

If you have an internet connection on the device, this should return a success. List of ZipKey networks will be stored in /etc/cirrent/zipkey_conf.bin and certificates in /etc/cirrent/certs/ directory. If you do not have an internet connection, the script will get an error. You need to setup an internet connection manually on the device and run the script again. (Note: this script is only run when you are manually installing the Cirrent Agent on your Linux device. For production devices, the device credential will be pre-provisioned during manufacturing.)

## Configuring credentials for production devices

Every ZipKey-enabled device needs its own credential. On Linux devices, the Cirrent Agent reads the credential from a specially formatted credential file, or uses a library you provide to read the credential. For production devices, each device should be pre-provisioned with a unique credential as part of the manufacturing process. The credential must also be uploaded to the Cirrent cloud. You can find more information about Device IDs [here](device-provisioning-security-options).

### **Credential library**

The best approach to providing the credential to the Cirrent Agent is to implement a small library, _libcirrent_cred.so_, that the Cirrent Agent will call to get the device credential. This gives you complete control over how and where you store the credential (e.g. you can store them in encrypted form and decrypt them when the Cirrent Agent needs them). The API for _libcirrent_cred.so_ is defined in _ca_cred.h_, and an example implementation (that reads the credential from a credential file) is in _ca_cred.c_.

### **Credentials file**

If you do not wish to provide a library that the Cirrent Agent can call to retrieve the credential, you can generate the credentials.key file in the format that the Cirrent Agent supports, and the Cirrent Agent will read the credential directly from the credentials.key file. The credentials.key file includes the Device ID, Device secret, and Account ID. You should save the credentials to a text file with the following formatting:

[Device Credential]

DeviceId: DEVICE_ID

DeviceSecret: DEVICE_SECRET

AccountId: ACCOUNT_ID

A sample credentials.key file for a device with Device ID ZipKeyProduct123, Device Secret MyDeviceSecret, and belonging to Account ID 1312 looks like this:

[Device Credential]

DeviceId: ZipKeyProduct123

DeviceSecret: MyDeviceSecret

AccountId: 1312

You can download a sample credentials file here.

Once you have saved the file as "credentials.key", you should place the file into the configured directory for the Cirrent Agent to use.

### **Saving the credentials.key file to the device**

 You will have to save the credentials.key file to a directory called "keys" located in the same directory where you installed the Cirrent Agent files. For example, the Cirrent Agent installer package for the Raspberry Pi described [here](installing-the-cirrent-agent-ini-on-raspberry-pi) installs the Cirrent Agent to the directory "/etc/cirrent" (the location of the "cirrent" directory is specified in the Cirrent Agent configuration file described [here](device-provisioning-security-options)). For a Raspberry Pi, the keys are stored in a directory "keys" with a full path of "/etc/cirrent/keys" (this path will change depending on where you have installed the Cirrent Agent). After you copy over the credentials.key file, make sure it has the appropriate permissions. The file must be available for reading by a user running as root.
