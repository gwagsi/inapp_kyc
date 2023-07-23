# inapp_flutter_kyc
The inapp_flutter_kyc package is a powerful and easy-to-use plugin that brings essential Know Your Customer (KYC) functionalities to your Flutter applications. Designed to streamline user identity verification and enhance security, this package offers a comprehensive set of features for performing KYC checks seamlessly within your app.


## Features

### Liveness Detection:
The package allows you to perform real-time liveness detection using the device's camera. Ensure that the user is physically present during the KYC process, preventing fraudulent attempts.

### ID Scanning:
Utilize advanced computer vision techniques to extract information from official identification documents such as passports, driver's licenses, national IDs, and more. Accelerate the KYC process with reliable and accurate data extraction.

### Face Matching:
Enhance identity verification by comparing the facial features between the scanned ID image and the selfie image provided by the user.

### Customizable UI:
Tailor the user interface to match your app's branding and design seamlessly. Customize colors, fonts, and layouts to create a cohesive user experience.

### Privacy and Security:
We prioritize the privacy and security of your users. Our package implements industry-standard security measures to protect sensitive user data during the KYC process.

## Getting started
To get started with the ekyc_flutter package, follow these simple steps:
```
flutter pub add inapp_flutter_kyc
```
### Android
Add this before `<application></application>` in your android/app/src/main/AndroidManifest.xml
```
<uses-feature
        android:name="android.hardware.camera"
        android:required="false" />
    <uses-permission android:name="android.permission.CAMERA" />
```
in <activity> add this 
```
android:requestLegacyExternalStorage="true"
```
in your android/app/build.gradle make minSdkVersion 23
```
defaultConfig {
        minSdkVersion 23
    }
```

### Face match
For running face match go to project_directory/face_match_with_flask and run this (for ubuntu)
```
python3 face_match.py
```
for windows
```
python face_match.py
```
you will see something like this in your console 
```
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:5000
 * Running on http://10.0.3.50:5000
```
copy the last address and pass it in EkycServices().runFaceMatch function along with the two imagepath (selfie image and id image) like this

```
await EkycServices().runFaceMatch("http://10.0.3.50:5000", selfieImage?.path, imageAndText?.imagePath);
```