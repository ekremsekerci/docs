---
title: "Set Up the Apple Push Notification Server"
linktitle: "Apple Push Notification Server"
url: /howto8/mobile/setting-up-apple-push-notification-server/
weight: 30
---

## Introduction {#intro}

In order to proceed you need an Apple developer license and a device running Mac OS X.

This how-to assumes that you already have the app signing key with provisioning profile and can freely build and install your mobile app (if not, please refer to [this how-to](/howto8/mobile/publishing-a-mendix-hybrid-mobile-app-in-mobile-app-stores/)). Take into account that your App ID should use `Explicit App ID` and have `Push Notifications` turned on so you can receive push notifications with your app.

{{< figure src="/attachments/howto8/mobile/hybrid-mobile/push-notifications/setting-up-apple-push-notification-server/20217895.png" class="no-border" >}}

If this is not the case, you need to create new App ID with `Explicit App ID` and `Push Notifications` turned on. After following the steps below, you'll need to generate and download a new provisioning profile for this App ID and use it to rebuild the mobile app.

If everything is set up and you can build and deploy your application, you can proceed with setting up the push notifications server. To establish connectivity between your notification server and the Apple Push Notification service you will need either:

* An Apple Push Notification service key, or
* An Apple Push Notification service SSL certificate in the *.p12* format

## Option A: Using a key

Follow the steps below to obtain and set up an Apple Push Notifications key from Apple.

### Signing Into the Apple Developer Center

Sign in to Apple Developer and navigate to [https://developer.apple.com/account/ios/authkey/](https://developer.apple.com/account/ios/authkey/).

### Creating a Key

Click the **+** icon in the upper right of the screen. This will present you with a new form. Enter a descriptive name for this key, select the **Push Notifications service** checkbox, and then press **Contine**. On the next page, press **Confirm**.

### Downloading the Key

Press the download button and store the key in a secure place. Also, copy the **Key ID** for use in the next step.

### Configuring APNs in Your Application

For the last step, you need to configure APNs within your application. This can be done by signing into your application as a user with the Administrator role and navigating to the **PushNotifications_Administration** page that was set up in the [Setting Up the Project Security for Your Module](/howto8/mobile/implementation-guide/#setting) section of *How to Implement Push Notifications*.

For this purpose, do the following:

* Create a new APNs configuration, and choose a name for the new configuration
* Choose a topic for the new configuration (you can freely choose one)
    * Set the **Authentication Type** to **Token**
    * If you receive a "topic disallowed" error message, leave the topic field empty
* Add your Apple Push Notification service key
    * Enter your team ID as shown on the Apple developer website
    * Enter the key ID as copied during the previous step

## Option B: Using an SSL certificate

Follow the steps below to obtain and set up an Apple Push Notifications service SSL certificate from Apple.

### Signing in to the Apple Developer Center

Sign in to Apple Developer and select your app on [https://developer.apple.com/account/ios/identifier/bundle](https://developer.apple.com/account/ios/identifier/bundle).

### Choosing the Certificate Type

Click **Edit**, scroll to the **Push Notifications** section, and choose to configure either a **Development** certificate or a **Production** certificate. A Development certificate can only be used with iOS apps built and run in development mode. Production certificates can only be used with apps built and run in production mode.

### Creating the CSR File

The wizard now explains how to create a Certificate Signing Request (CSR). Read this description and press **Continue**. During the next step, you should be asked for your CSR file. You may use the same CSR you used to create the app signing certificate. If you do not have one, please follow the instructions as shown below.

{{< figure src="/attachments/howto8/mobile/hybrid-mobile/push-notifications/setting-up-apple-push-notification-server/20217898.png" class="no-border" >}}

### Downloading the Certificate

Download your Apple Push Notification service SSL certificate and add it to your Keychain.

This certificate needs to be converted into the *.p12* format. If you do not know how to do this, refer to Apple's [What is app signing?](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html).

### Configuring APNs in Your Application

For the last step, you need to configure APNs within your application. This can be done by signing into your application as a user with Administrator role and navigating to the **PushNotifications_Administration** page that was set up in the [Setting Up the Project Security for Your Module](/howto8/mobile/implementation-guide/#setting) section of *How to Implement Push Notifications*.

To configure your APNs, complete the following steps:

* Create a new APNs configuration, and choose a name for the new configuration
* Choose a topic for the new configuration (you can freely choose one)
    * Set the **Authentication Type** to **Certificate**
    * Choose the **Stage** that corresponds to the type of certificate you have created
* Add your Apple Push Notification service SSL certificate in the *.p12* format
    * Enter the password that you used during creation of the certificate

## Read More

* [Implement Push Notifications](/howto8/mobile/implementation-guide/)
* [Publish a Mendix Hybrid Mobile App in Mobile App Stores](/howto8/mobile/publishing-a-mendix-hybrid-mobile-app-in-mobile-app-stores/)
