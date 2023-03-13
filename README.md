# Proguard Rules

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

**Note: — These rules will work only in release mode.**
