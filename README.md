# Proguard Rules For Flutter

ProGuard is nice to have in your app because it helps to shrink, obfuscate and optimize your flutter app.


## Step 1

First, we will enable shrinking and obfuscation in the build file. Find build.gradle file which sits inside **/android/app/** folder and insert these lines in **buildTypes**.

```
   buildTypes {
        release {
            signingConfig signingConfigs.release
            minifyEnabled true
            shrinkResources true

            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
```

![Screenshot 2023-03-13 at 10 06 24 AM](https://user-images.githubusercontent.com/77187473/224609312-d2d818b7-e953-41a0-bb08-65b3a82a1f53.png)



## Step 2

In this step we enable R8 in gradle.properties which is located at **/android folder**.

![Screenshot 2023-03-13 at 9 23 58 AM](https://user-images.githubusercontent.com/77187473/224607788-8c03a2ab-0da8-4737-9c26-dd1475a5dd7a.png)
## Step 3

In this step we will create a configuration which will preserve entire Flutter wrapper code. Create /android/app/proguard-rules.pro file and insert inside

```
#Flutter Wrapper
-keep class io.flutter.app.** { *; }
-keep class io.flutter.plugin.**  { *; }
-keep class io.flutter.util.**  { *; }
-keep class io.flutter.view.**  { *; }
-keep class io.flutter.**  { *; }
-keep class io.flutter.plugins.**  { *; }

# Add project specific ProGuard rules here.
# By default, the flags in this file are appended to flags specified
# in /usr/local/google/home/samstern/android-sdk-linux/tools/proguard/proguard-android.txt
# You can edit the include path and order by changing the proguardFiles
# directive in build.gradle.
#
# For more details, see
#   http://developer.android.com/guide/developing/tools/proguard.html

# Add any project specific keep options here:

# If your project uses WebView with JS, uncomment the following
# and specify the fully qualified class name to the JavaScript interface
# class:
#-keepclassmembers class fqcn.of.javascript.interface.for.webview {
#   public *;
#}

# Uncomment this to preserve the line number information for
# debugging stack traces.
-keepattributes SourceFile,LineNumberTable

# If you keep the line number information, uncomment this to
# hide the original source file name.
#-renamesourcefileattribute SourceFile

# Keep custom model classes
-keep class com.google.firebase.** { *; }


# To ignore minifyEnabled: true error
# https://github.com/flutter/flutter/issues/19250
#https://github.com/flutter/flutter/issues/37441
-ignorewarnings
-keep class * {
    public private *;
}
```

**Note: — These rules will work only in release mode.**
