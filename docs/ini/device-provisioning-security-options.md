# Device Provisioning & Security Options

Cirrent authenticates each unique device both when the device joins a ZipKey hotspot and when the device connects to the Cirrent API. The Wireless Connection Manager handles this authentication so the device code does not need to do anything. Each device needs to be provisioned both in the Cirrent Cloud and in the device at the time of manufacture. The system is flexible enough to be compatible with most existing authentication mechanisms so product companies don't have to change their device provisioning process.

Options for authentication include:

1.  **Secure certificates:**  a unique signed certificate is provisioned to each device at the time of manufacture
2.  **Shared secret**: a unique device id and secret is provisioned to each device at the time of manufacture
3.  **Temporary credentials:**  a unique device id is provisioned to each device at the time of manufacture, and the device generates a unique temporary credential that it uses until it receives a permanent shared secret.

We'll go through the details of each one of these options below.

Secure Certificates

The most secure method of securing the device is through a unique, per-device certificate. Contact Cirrent directly if you would like to implement this option.

Shared Secret

The second way to provision devices is to put a unique shared secret on each device. The combination of the shared secret and the device id allow Cirrent to authenticate the device. To provision the device:

-   Register the device id and the shared secret in the Cirrent Cloud
-   Put the device id and the shared secret in the CA configuration

Temporary Credentials

The third way to provision devices is to use a provisioning key that is shared across many devices. Cirrent's service uses this provisioning key and the device id to generate a temporary shared secret unique to the device, and uses that to log into ZipKey hotspots and the Cirrent cloud. On the first connection, the device is then issued a shared secret, which the device uses from that time forward. To provision your device using temporary credentials:

-   Make sure you have a Provisioning Key
-   Put the device id and the Provisioning Key in the CA configuration ([learn more here](starting-ca-using-temporary-credentials))
