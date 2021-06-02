Buid libjpeg-turbo-android-lib
==================

1.To get started, ensure you have the latest NDK
You must configure the path of JDK and Android SDK.

    echo "export ANDROID_HOME='Your android ndk path'" >> ~/.bash_profile

    source ~/.bash_profile


2.Build libjpeg-turbo.so

    cd ../libjpeg-turbo-android/libjpeg-turbo/jni

    ndk-buld

3.You can get libjpegpi.so in 

     ../libjpeg-turbo-android/libjpeg-turbo/libs/armeabi


4.Copy libjpegpi.so to ../bither-android-lib/libjpeg-turbo-android/use-libjpeg-trubo-adnroid/jni

     cd ../bither-android-lib/libjpeg-turbo-android/use-libjpeg-trubo-adnroid/jni

     ndk-build

5.You can get libjpegpi.so and libpijni.so 


6.Use libjpeg-turbo in java 

     static {

        System.loadLibrary("jpegpi");
       
        System.loadLibrary("pijni");

     }
 and you must use class of "com.pi.common.util.NativeUtil"

7.在ndk（v17）开始已经不在支持mips、armeabi、mips64等CPU架构只支持armeabi-v7a, arm64-v8a, x86, x86_64。而自己工程的ndk版本是:/Library/Android/sdk/ndk/22.1.7171670，因此报错
解决办法：

(1).在build.gradle中移除armeabi mips等ABI配置，缺点就是不支持armeabi mips等ABI，即生成不了对应的so文件，不完美
(2).要兼容armeabi mips等ABI，需修改ndk的版本降级到v16 ，并替换AS里NDK路径即可.
