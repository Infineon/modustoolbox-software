# Android Sample Application

Along with the Cirrent Android SDK, we will provide you with the source code to a sample application that uses the Cirrent SDK to onboard a device onto the user's private Wi-Fi network, and manage the devices associated with the user's account. The Cirrent Android sample application is written in Java, and provided in source code form to help you while you are modifying your app to incorporate the Cirrent SDK. The Cirrent sample app shows the on-boarding flow for a typical connected product, and also shows how you can use the Cirrent SDK to manage the connected products associated with your user's account.

The main areas of functionality that you should look at are:

-   Fragments - these are some screens for the sample app that call the main methods in the CirrentService

-   LoginFragment - this is the first screen where the user logs in. You should replace this with a login to your cloud. It logs the user in, and gets a SEARCH token that will be used to authenticate your app to the Cirrent cloud. See the article on  [tokens](analytics-token-generation)  for more information on the tokens that your app will need to pass into the Cirrent SDK.
-   FindDeviceFragment - this is the screen where the user searches for nearby devices of the correct type that have been powered on recently and are not yet associated with a user account.
-   SetupDeviceManuallyFragment, SetupDeviceAutomaticallyFragment, SetupDeviceViaSoftApFragment - these are the screens that enable the user to choose which network they would like the connected product to join
-   SendPrivateCredentialsFragment - this fragment sends the private credentials via the Cirrent cloud, and waits for the device to confirm that it has JOINED the private network.
-   SendProviderCredentialsFragment - this fragment instructs the Cirrent cloud to get the private network credentials from the provider, and then waits for the device to confirm that it has JOINED the private network
-   SendCredentialsViaSoftApFragment - this fragment sends the private credentials over the softAP network to the device and waits for the device to confirm that it has JOINED the private network.
-   PollUserActionFragment - if the onboarding process requires the user to confirm they are in possession of the product, by taking some action on the product (e.g. pressing a button), this fragment waits to get confirmation that the action was taken on the device

-   SuccessFragment - this is the screen that is shown when the device has successfully joined the user's private network. This screen will typically be replaced with the main screen for your connected product.

-   ProductCloudApi (com.sampleapp.net.ProductCloudApi) - this is an example of a cloud that will issue tokens to authorize the app to call the Cirrent service. The product cloud also keeps track of which devices have been bound to the user's account. You should replace this API with calls to your cloud.

You can download the sample app from Google Play at  [https://play.google.com/store/apps/details?id=com.cirrent.ZipKeyApp](https://play.google.com/store/apps/details?id=com.cirrent.ZipKeyApp)
