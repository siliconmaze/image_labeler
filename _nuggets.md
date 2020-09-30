# Setting Up Flutter example that uses Firebase/CloudVision API

## Installing Android Studio et al
- Install Android Studio on my FL Laptop (Non WSL as I do not have WSL2)
- Get Visual Studio Setup for Flutter

### install Android Studio
https://developer.android.com/studio
Install takes some time as it has to download and install after the inital bootstrapper GUI.
 - FJ laptop is locked down, so I have to approve various stages of install.

 ```s
 Intel® HAXM installation failed. To install Intel® HAXM follow the instructions found at: https://software.intel.com/android/articles/installation-instructions-for-intel-hardware-accelerated-execution-manager-windows
Installer log is located at C:\Users\ROBINSONST\AppData\Local\Temp\haxm_log.txt
Installer log contents:
=== Logging started: 29/09/2020  08:43:40 ===
This computer does not support Intel Virtualization Technology (VT-x) or it is being exclusively used by Hyper-V. HAXM cannot be installed. 
Please ensure Hyper-V is disabled in Windows Features, or refer to the Intel HAXM documentation for more information.
```

I then had to download and instal the Flutter SDK...

`https://flutter.dev/docs/get-started/install/windows`

I extracted it into c:\src, then added to windows path.

for example: 

`C:\src\flutter_windows_1.20.4-stable\flutter\bin`

I then ran flutter doctor

```s
Doctor summary (to see all details, run flutter doctor -v):
[√] Flutter (Channel stable, 1.20.4, on Microsoft Windows [Version 10.0.18362.1016], locale en-GB)

[!] Android toolchain - develop for Android devices (Android SDK version 30.0.2)
    X Android licenses not accepted.  To resolve this, run: flutter doctor --android-licenses
[√] Android Studio (version 4.0)
[!] VS Code (version 1.49.1)
    X Flutter extension not installed; install from
      https://marketplace.visualstudio.com/items?itemName=Dart-Code.flutter
[!] Connected device
    ! No devices available
```

`flutter doctor --android-licenses`


I was able to create a new Aplication and deploy see the basic flutter app in AzureDevOps HOH repo (flutter project/repo). it took ages, the platform is really slow!
Later that day I aspke with Seville and they also said it is slow and horrible, but it is what it is.

====

I update the details of my experience on Wednesday 30-September-2020 as a fork from the followng article

https://heartbeat.fritz.ai/face-detection-in-flutter-using-firebases-ml-kit-57a7a9078c3f

I then forked his repo into my silicon maze git hub, so I could commit code.

https://github.com/siliconmaze/image_labeler

I found that before the aplication was re-built, it remembers the devices of the last build (ie previous devlopers actual mobile devices).
I could not figure out the way to fix this is? L:ater below I re-built the entire project after a `fluttr clean` and then restarted the entire laptop, then for come reason f`lutter devices` reported my physical samsung and AVD pixel device. I also learned that we can use adb from platform tools folder of Androijd SDK. I installed everyting on windows natively so I can use via CMD prompt and GitBash. SWL is not an option!

I also had to enable the GCP Cloud vision API in my c`loudy.dog` GCP account, enable billing for the firebas project, and also update the code to rflect the corregt paclage with my associated app rgistration in firebas console.


__Note:__ The issue with projects checked in by other devlopers in their repos they have their config, so what I get is a bunch of outdated configs or other bullshit. I could not figure out how to remove the previous developers modile device definitions as I said above? 

When I tried Android Studoi first, it made a mess of things with so many added files, when I later did all of this in Visual Studio code, it was alot simpler to see the wood for the trees.

Today I purchased the Flutter Devlopment course, but after some thought I should be thinking in terms of React Native, so I can learn something abou this project. So toight 30th Sepm 2020 I wil purchse the udeny course for Reac tMobile fom Maximilian S.

I have purchased these today, and so I have 

- Flutter & Dart - The Complete Guide [2020 Edition] - Maximilian Schwarzmüller,
- React Native - The Practical Guide [2020 Edition] - Maximilian Schwarzmüller, Online Education
- The Complete React Native + Hooks Course - Stephen Grider, Engineering Architect

I am going to claim these from Fujitsu.

====

Notes from the mornings efforts...

I then tried to see if I could get the project working in visual Studio?
Since I am using WSL 1 I had to install manually in windows, do not use WS1 t host Andrond Studio or flutter, it is just a complex waste of time. Either OSX, windows pure of Linux , not WSL* it will have too many issues!

I then tried using git bash as this is the way to navigate etc

I have flutter in my path from the Windows install of fluter above, so lets try and locate it withnig git bash?
I am in a new clone of thr repo:


cd ~/local-repos/github/
git clone git@github.com:siliconmaze/image_labeler.git
cd image_labeler
~/local-repos/github/image_labeler



I then ran flutter device -v
fior vebose:
 and I get 


$ flutter devices -v
[ +118 ms] executing: [C:\src\flutter_windows_1.20.4-stable\flutter/] git -c log.showSignature=false log -n 1 --pretty=format:%H
[ +124 ms] Exit code 0 from: git -c log.showSignature=false log -n 1 --pretty=format:%H
[        ] fba99f6cf9a14512e461e3122c8ddfaa25394e89
[        ] executing: [C:\src\flutter_windows_1.20.4-stable\flutter/] git tag --contains HEAD
[ +389 ms] Exit code 0 from: git tag --contains HEAD
[        ] 1.20.4
[   +8 ms] executing: [C:\src\flutter_windows_1.20.4-stable\flutter/] git rev-parse --abbrev-ref --symbolic @{u}
[ +105 ms] Exit code 0 from: git rev-parse --abbrev-ref --symbolic @{u}
[        ] origin/stable
[        ] executing: [C:\src\flutter_windows_1.20.4-stable\flutter/] git ls-remote --get-url origin
[  +78 ms] Exit code 0 from: git ls-remote --get-url origin
[        ] https://github.com/flutter/flutter.git
[ +146 ms] executing: [C:\src\flutter_windows_1.20.4-stable\flutter/] git rev-parse --abbrev-ref HEAD
[ +109 ms] Exit code 0 from: git rev-parse --abbrev-ref HEAD
[        ] stable
[ +106 ms] Artifact Instance of 'AndroidMavenArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'AndroidGenSnapshotArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'AndroidInternalBuildArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'IOSEngineArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'FlutterWebSdk' is not required, skipping update.
[   +4 ms] Artifact Instance of 'WindowsEngineArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'MacOSEngineArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'LinuxEngineArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'LinuxFuchsiaSDKArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'MacOSFuchsiaSDKArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'FlutterRunnerSDKArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'FlutterRunnerDebugSymbols' is not required, skipping update.
[  +15 ms] Artifact Instance of 'MaterialFonts' is not required, skipping update.
[        ] Artifact Instance of 'GradleWrapper' is not required, skipping update.
[        ] Artifact Instance of 'AndroidMavenArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'AndroidGenSnapshotArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'AndroidInternalBuildArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'IOSEngineArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'FlutterWebSdk' is not required, skipping update.
[        ] Artifact Instance of 'FlutterSdk' is not required, skipping update.
[        ] Artifact Instance of 'WindowsEngineArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'MacOSEngineArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'LinuxEngineArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'LinuxFuchsiaSDKArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'MacOSFuchsiaSDKArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'FlutterRunnerSDKArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'FlutterRunnerDebugSymbols' is not required, skipping update.
[        ] Artifact Instance of 'IosUsbArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'IosUsbArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'IosUsbArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'IosUsbArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'IosUsbArtifacts' is not required, skipping update.
[        ] Artifact Instance of 'FontSubsetArtifacts' is not required, skipping update.
[  +34 ms] executing: C:\Users\ROBINSONST\AppData\Local\Android\sdk\platform-tools\adb.exe devices -l
[ +173 ms] List of devices attached
           RFCMC004CZZ            device product:d2xeea model:SM_N976B device:d2x transport_id:2
           emulator-5554          device product:sdk_gphone_x86_arm model:sdk_gphone_x86_arm device:generic_x86_arm transport_id:1
[   +7 ms] 2 connected devices:

[   +7 ms] C:\Users\ROBINSONST\AppData\Local\Android\sdk\platform-tools\adb.exe -s RFCMC004CZZ shell getprop
[ +171 ms] ro.hardware = exynos9825
[        ] ro.build.characteristics = phone
[   +2 ms] C:\Users\ROBINSONST\AppData\Local\Android\sdk\platform-tools\adb.exe -s emulator-5554 shell getprop
[ +131 ms] ro.hardware = ranchu
[   +5 ms] SM N976B (mobile)           • RFCMC004CZZ   • android-arm64 • Android 10 (API 29)
[        ] sdk gphone x86 arm (mobile) • emulator-5554 • android-x86   • Android 11 (API 30) (emulator)
[   +5 ms] executing: C:\Users\ROBINSONST\AppData\Local\Android\sdk\platform-tools\adb.exe devices -l
[ +125 ms] List of devices attached
           RFCMC004CZZ            device product:d2xeea model:SM_N976B device:d2x transport_id:2
           emulator-5554          device product:sdk_gphone_x86_arm model:sdk_gphone_x86_arm device:generic_x86_arm transport_id:1
[  +12 ms] "flutter devices" took 709ms.
[  +63 ms] ensureAnalyticsSent: 57ms
[   +2 ms] Running shutdown hooks
[        ] Shutdown hooks complete
[        ] exiting with code 0
G03+RobinsonSt@G02UKXN08227:~/local-repos/github/image_labeler
$

===


cd ~/AppData/Local/Android/Sdk/platform-tools
adb.exe kill-server
adb.exe -start-server

./adb.exe devices
List of devices attached
RFCMC004CZZ     device
emulator-5554   device

====

This does not remove the flutter devices?

====


I decide to restart my machine lol

This fixed the issue lol.

===

I then on GitBash VSCode installed the Flutter plugin

Flutter = dart-code.flutter

===

I am now see that the project does not know where the flutter SDk is located?

The SDK is set by ...

https://flutter.dev/docs/development/tools/vs-code

I then view/command-pallete `flutter: doctor`

all was good, then tried to run/debug

```s
Target of URI doesn't exist: 'package:flutter/material.dart'
Try creating the file referenced by the URI, or Try using a URI for a file that does exist.
```


then I ran in command prompt 

`flutter: packages get`

It hen in status bar I selected the Smasun devicem, and voila it loaded lol, this is cool, I have acheievd smoething!


```s

batchAnnotateImages call failed with error: {"code":403,"errors":[{"domain":"usageLimits","message":"Cloud Vision API has not been used in project 1071487044702 before or it is disabled. Enable it by visiting https://console.developers.google.com/apis/api/vision.googleapis.com/overview?project=1071487044702 then retry. If you enabled this API recently, wait a few minutes for the action to propagate to our systems and retry.","reason":"accessNotConfigured","extendedHelp":"https://console.developers.google.com"}],"message":"Cloud Vision API has not been used in project 1071487044702 before or it is disabled. Enable it by visiting https://console.developers.google.com/apis/api/vision.googleapis.com/overview?project=1071487044702 then retry. If you enabled this API recently, wait a few minutes for the action to propagate to our systems and retry.","status":"PERMISSION_DENIED"}
Application finished.
```

Now i will update the `google-services.json` downloaded from  my firebase console:

```s
https://console.firebase.google.com/project/facerecognitionflutter/overview
https://console.firebase.google.com/project/facerecognitionflutter/settings/general/android:ml.rishitdagli.face_recog
```


also enabled cloud vision in GCP account

```s
https://console.cloud.google.com/home/dashboard?project=facerecognitionflutter&pli=1
```


```s
Exception has occurred.
PlatformException (PlatformException(imageLabelerError, 403 Forbidden
{
  "code": 403,
  "errors": [
    {
      "domain": "usageLimits",
      "message": "Cloud Vision API has not been used in project 1071487044702 before or it is disabled. Enable it by visiting https://console.developers.google.com/apis/api/vision.googleapis.com/overview?project=1071487044702 then retry. If you enabled this API recently, wait a few minutes for the action to propagate to our systems and retry.",
      "reason": "accessNotConfigured",
      "extendedHelp": "https://console.developers.google.com"
    }
  ],
  "message": "Cloud Vision API has not been used in project 1071487044702 before or it is disabled. Enable it by visiting https://console.developers.google.com/apis/api/vision.googleapis.com/overview?project=1071487044702 then retry. If you enabled this API recently, wait a few minutes for the action to propagate to our systems and retry.",
  "status": "PERMISSION_DENIED"
}, null))
```

We can see the project is still trynig to connect to the previous project id ?

I ran flutter clean

Ahh ..

`No matching client found for package name 'com.example.object_detection'`

I need to update the json config in firebase lol with the correct package name to match project here in the code.

I cheated and updated build,grade app id

from 
`com.example.object_detection`
to
`ml.rishitdagli.face_recog`, because this is what ws registered in the firebase app already lol.


Now I get firebase billing error:

```s
Exception has occurred.
PlatformException (PlatformException(imageLabelerError, If you haven't set up billing, please go to Firebase console to set up billing: https://console.firebase.google.com/u/0/project/_/overview?purchaseBillingPlan=true. If you are specifying a debug Api Key override and turned on Api Key restrictions, make sure the restrictions are set up correctly, null))
```

Since I as usnig CGP that was an old trial account, I am now having to pay LOL, so I needed to update billing.


====

Now the project is working, I am look at maknig this work better, have a better naming conventions, and better documentation.

Note, I am not referring to the proejct in this repo, but the project in the gitbash FJ Windows laptop `G03+RobinsonSt@G02UKXN08227:~/local-repos/github/image_labeler` repo, and is in Azuer DevOps HOH

I am saving the code, and going to start the flutter course now. I happy with the basic premise of setup, tools, and SDK nuggets and Firebase, and GCP etc. For learnig to code in SVCode is better as a programmer because Android Studio is very complex and bloated. I guess I will need to deal with this in time, and I wil become a pro eventually, but I have a long way to go as a Flutter progammer!

==== 

One thing I am doing is to charge Fj for all my Mobile App Learning costs!





