# iOS Sample Application


The Cirrent iOS sample application is provided in source code form to help you while you are modifying your app to incorporate the Cirrent SDK. The Cirrent sample app has two main parts to it - a live flow that can be used to onboard a ZipKey-enabled product, and a demo flow that mimics all the screens without actually onboarding a ZipKey-enabled product. The demo flow is useful to see what the user experience is, without needing to have a real ZipKey product to onboard. The live flow implement the on-boarding flow for a typical connected product, and also shows how you can use the Cirrent SDK to manage the connected products associated with your user's account.

The main areas of functionality that you should look at are:

-   Controllers - these are the main screens for the live flow

-   ProductsViewController - this is the first screen where the user logs in. It will show any products associated with the user's account, and give an option to add a new product.
-   FindDeviceViewController - this is the screen where the user searches for nearby discoverable devices of the correct type that have been powered on recently
-   AddDeviceViewController - this is the screen where the user is shown the list of nearby devices that are not yet associated with any user account. The user selects the one they wish to bind to their account.
-   SetupDeviceAutomaticallyViewController - If the phone is on a private network for which the broadband provider has credentials, the user can be given an option for Cirrent to get the private network credentials from the broadband provider, saving the user the trouble of entering them manually. Or the user can choose to enter the private network credentials manually.
-   SendProviderCredentialsViewController -this is the screen where the app requests that Cirrent get the credentials from the broadband provider. The user is given status updates as the device joins the private network, using the credentials that came from the provider.
-   ChooseNetworkViewController - this is the screen where the user selects their private network and manually enters the pre-shared key.
-   SendPrivateNetworkViewController - this is the screen where the credentials are sent to the Cirrent cloud. The user is given status updates as the device joins their private network, when the credentials came from the user.
-   SuccessViewController - this is the screen that is shown when the device has successfully joined the user's private network. This screen will typically be replaced with the main screen for your connected product.
-   ConnectViaSoftApLoadingViewController - this is the screen that is shown when the device cannot be found via the cloud, and the user needs to move their phone over to the SoftAP network.
-   SendCredentialsViaSoftApViewController - this is the screen where the user is given status updates as the device joins the private network, with credentials sent via softAP. When the device joins the private network, and the softAP network goes away, the app binds the device in the sample cloud and the Cirrent cloud, to complete the onboarding process.
-   DeviceInfoActivityViewController - this is the screen that shows the devices already associated with this user's account, from where the user can set a friendly name for the device or add new networks.
-   KnownNetworksViewController - this is the screen where the user can see the private networks already configured in their device.
-   AddNetworkController - this is the screen where the user can add a new network to a device already associated with their account.
-   IdentifyActionViewController - if the device supports an identify action, this is the screen that tells the user what the action will be, and gives them a way to trigger the action
-   PollUserActionViewController - if the device supports a user action, this is the screen that waits to confirm the user action was executed before allowing the user to bind the device to their account

-   Sample Cloud - the Requester directory contains methods that will call the sample cloud to get tokens to authorize the app to use the Cirrent service. The sample cloud also keeps track of which devices have been bound to the user's account. You should replace these Requester calls with calls to your cloud.

If you wish to build the sample app, you will need to install CocoaPods, using the following commands:

`sudo gem install cocoapods`

`pod install`

CocoaPods is required for AlamoFire, EVReflection and RxBluetooth (which are used in the Cirrent sample app).

You can also download the sample app from the App Store at [https://itunes.apple.com/ca/app/zipkey-dev-tool/id1265896377](https://itunes.apple.com/ca/app/zipkey-dev-tool/id1265896377)
