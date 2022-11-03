# Android crash debug


 ~_Library_Android_sdk_platform-tools/adb kill-server # to restart the server and catch the Android emulator

~_Library_Android_sdk_platform-tools/adb devices # take device ID from there

~_Library_Android_sdk_platform-tools_adb logcat -v threadtime [device ID] > ~_Desktop/android-debug.log

 do the actions leading to failure
Ctrl + C once done.

https://www.hexnode.com/mobile-device-management/help/obtain-android-device-logs-using-windows-and-mac/