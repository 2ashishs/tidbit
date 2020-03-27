# Android

* **Creating avd from command-line**
```
avdmanager create avd -n MyAvdName -d <device-id> -c <sd-card size, e.g. 1000M for 1000MB> -k 'system-images;android-27;google_apis_playstore
;x86'
```
> Refer to **avdmanager -h create avd** for more help

* **View GA events in terminal**
```
adb shell setprop log.tag.GAv4 DEBUG
adb logcat -s GAv4
```

* **Launch Deeplink from terminal**
```
adb shell am start -W -a android.intent.action.VIEW -d "myApp://myDeeplink" appPackageName
```

* **Launch App from terminal**
```
adb shell am start -n "appPackageName/appPackageName.launcherActivity" - a android.intent.action.MAIN -c android.intent.category.LAUNCHER
```
