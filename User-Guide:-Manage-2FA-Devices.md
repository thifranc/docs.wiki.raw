# 2FA device settings
You can manage the devices that you use for 2-Factor-Authentication with the liquid-bundle. For example you might want to change devices, if you get a new mobile phone or add a second device to authenticate with.
To open the settings click the "2FA settings" button on the homepage.

![2FA Settings](https://github.com/liquidinvestigations/docs-img/blob/7e2a6539793b6cea2349bb9ccbeddb4575df9001/2fa_settings_1.png)

You will see a list of devices that are currently registered. The device named like your username is the first device you registered when logging in. You have three options to manage your devices.

![2FA device list](https://github.com/liquidinvestigations/docs-img/blob/7e2a6539793b6cea2349bb9ccbeddb4575df9001/2fa_settings_options.png)

## Change device
Click the change device button.

![Change device form](https://github.com/liquidinvestigations/docs-img/blob/7e2a6539793b6cea2349bb9ccbeddb4575df9001/2fa_settings_3.png)

Then enter your current password, a valid OTP-Token (form one of your registered devices) and a name for the new device. After clicking change, you will be redirected and a new QR code is presented to you. 

![QR Code 2FA](https://github.com/liquidinvestigations/docs-img/blob/7e2a6539793b6cea2349bb9ccbeddb4575df9001/2fa_settings_4.png)

Use this QR-Code to register a new Account in your OTP-App on the new device. After that enter a token from the new device to complete the change.

**Be careful:** This will remove all devices from the list, but the new one. All other devices won't work for authentication afterwards.

## Add new device
Click the add new device button.
Enter your password, a valid OTP token and a name for your new device.

![Add 2FA device form](https://github.com/liquidinvestigations/docs-img/blob/7e2a6539793b6cea2349bb9ccbeddb4575df9001/2fa_settings_add.png)

After clicking "Add" you will be redirected to a QR-Code again, that you can use to register the account in your App.

If you look at the 2FA settings again, after adding a new device you should see two devices in the list.

![2FA multiple devices](https://github.com/liquidinvestigations/docs-img/blob/7e2a6539793b6cea2349bb9ccbeddb4575df9001/2fa_settings_6.png)

## Remove device
Click the "Remove devices" button. 

![2FA remove device form](https://github.com/liquidinvestigations/docs-img/blob/7e2a6539793b6cea2349bb9ccbeddb4575df9001/2fa_settings_rm_1.png)

Enter your password and a valid OTP-Token from any of your devices.

**Be careful:** All the devices but the one you use to create that OTP-token are deleted from the list and won't work afterwards!