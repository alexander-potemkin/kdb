# BitRise build HowTo

## iOS

certificate import - through the XCode’s preferences, manage certificates -> make sure the distribution one is there

p12 certificate (for iOS! distribution) export: [iOS - Creating a Distribution Certificate and .p12 File – Mag+ Designd Support](https://support.magplus.com/hc/en-us/articles/203808748-iOS-Creating-a-Distribution-Certificate-and-p12-File)


get.udid.io

Diawi pass: 1QWH

# Android

react-native bundle --platform android --dev false --entry-file index.js --bundle-output android_app_src_main_assets_index.android.bundle --assets-dest android_app_src_main/res

export JAVA_HOME=`/usr/libexec/java_home -v 1.8`

._android_gradlew ":app:assembleRelease"

./gradlew bundleRelease 

===

Android Studio & Android SDK download


# DO NOT DO THIS: https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html JDK 1.8 download

brew tap AdoptOpenJDK/openjdk
brew cask install adoptopenjdk8

# /usr/libexec/java_home -V
# export JAVA_HOME=`/usr/libexec/java_home -v 1.8`
# java -version

# https://stackoverflow.com/questions/40248265/how-to-set-android-sdk-root-in-mac

export JAVA_HOME=`/usr/libexec/java_home -v 1.8`
export ANDROID_HOME=~_Library_Android/sdk
export ANDROID_SDK_ROOT=~_Library_Android/sdk
export ANDROID_AVD_HOME=~_.android_avd
java -version


# npm i
# sed -i.bak 's/import android.support.annotation.Nullable/import androidx.annotation.Nullable/' ./node_modules/react-native-picker/android/src/main/java/com/beefe/picker/PickerViewModule.java
# ./gradlew ":app:assembleRelease"


npm i react-native-simple-markdown

## ./gradlew bundleRelease

my-upload-key.keystore
> Keystore file '_Users_vagrant_git_android_app_$BITRISEIO_ANDROID_KEYSTORE_URL' not found for signing config 'release'.  


Create API at:

https://console.cloud.google.com/iam-admin/serviceaccounts?project=api-6936492331622665731-657664 --> make sure to assign role

https://medium.com/@bitrise/how-to-deploy-your-android-app-to-google-play-store-441bc8a5bb61
		- [ ] google-play-deploy@3:
        inputs:
				- [ ] service_account_json_key_path --> IT IS NOT A SECRET
BITRISEIO_SERVICE_ACCOUNT_JSON_KEY_URL