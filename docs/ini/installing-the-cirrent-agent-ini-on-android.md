# Installing the Cirrent Agent (INI) on Android

1.  Create a new provisioning key by visiting the Cirrent Console.
    -   [Learn more about the provisioning key here](starting-ca-using-temporary-credentials).
    -   Note down the provisioning key and secret. You will need this information later.
2.  Extract the  [ca_android_1.50.tar.gz](../files/ca_android_1.50-ini.tar.gz) tar file to your local machine. The tar file contains the Cirrent APK and a Cirrent directory. It is compatible with Android versions 6 and above.
3.  Connect to Android using adb by executing the following command. You will need to enable USB debugging on your Android device. Please use adb version v1.0.39 or newer  
    ```
    adb connect IP_ADDRESS_OF_ANDROID_ON_SAME_SUBNET
    ```
4.  Install the APK and start the service. You will need to include your provisioning key, unique identifier, account id, serial number, and device type id.
5.  ``` adb install PATH_TO_CIRRENT_APK ```
    
6. ``` am startservice -n com.cirrent.agent/.CirrentAgentService -e acc_id 0000 -e device_type_id 0000 -e prov_key abc -e prov_secret abc -e serial_number abc ```
    
7.  The cirrent service will be started in the background. You can log into the Console and check the INI data on the device explorer page by entering the serial number passed in step 6 and click the Explore button.
8.  If you don't see the updates on the device explorer page,
    -   Make sure that the Cirrent service is running by typing in "ps -A | grep cirrent" in adb shell, if not then run the command in step 6 again.
    -   Disable SELINUX on the Android box
    -   If you still have trouble getting things up and running contact [support@cirrent.com](mailto:support@cirrent.com) with the adb logcat output of your Android device and the Android version of your device.

-   [ca_android_1.50-ini.tar.gz](../files/ca_android_1.50-ini.tar.gz)
    
    4 MB  [Download](../files/ca_android_1.50-ini.tar.gz)
