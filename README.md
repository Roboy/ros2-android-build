# ros2-android-build

Build rcljava for android.

Customized for [ros2-loomo-controller](https://github.com/Roboy/ros2-loomo-controller) project.  

## Versions & Envs

- NDK: android-ndk-r23b
- ABI: x86_64  
- Android API Level(minSdkVersion): android-21

## ROS2 java version  

https://raw.githubusercontent.com/ros2-java/ros2_java/434e6f55253bfe2cb9ce34799fe548bbf4998d0e/ros2_java_android.repos


## Steps to build

### 1. Build docker image
```
# docker build -t ros2java-android-build ./

docker build --platform linux/amd64 -t ros2java-android-build ./
```

### 2. Build
```
# python3 run.py ./out/soOut ./out/jarOut --srcDir ../src 

python3 run.py ../ros2-loomo-controller/app/src/main/jniLibs/x86_64 ../ros2-loomo-controller/app/libs  --srcDir ../ros2-loomo-controller/app/src
```

First and Second argument specifies where to copy build results.  
Eg. Specify `libs` and `jniLibs` dir of your Android project to copy `.jar` file and `.so` files.  
Copying `.so` files to the correct directory under `.../main/jniLibs/` is important. You should match the target ABI here.

`--srcDir` option is using for adding packages other than ros2 java related packages, for example your own message package.  
You can just specify your `src` dir which contains multiple packages. This option is not mandatory.


## Note1   
↓Android project structure example.  
```
app
 -libs
    - .jar files
 - src
    - main
        - java
        - jniLibs
            - arm64-v8a
                - .so files
            - x86_64
                - .so files
        - res
        - AndroidManifest.xml

```
Refer to example project: https://github.com/YasuChiba/ros2-android-test-app

## Note2 
Build `ros2_android` and `ros2_android_examples` by this Dockerfile is currently not supported.  
Please build your android app by using Android Studio.
