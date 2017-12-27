# udemy-albums

instalar el cli de react usando npm:
    - npm install -g react-native-cli

crear proyecto:
react-native init nombre-proyecto

abrir el proyecto android con Android Studio y ver que no hay errores

troubleshooting, mirar estas cosas que afectan a que salgan errores al ejecutar el comando react-native run-android
   - control+alt+shift+s y setear:
   -      en Project, Gradle version 3.3 y Android plugin version: 2.3.3
   -      archivo build.gradle del proyecto (no de app) y añadir el snipet:
   -               url "$rootDir/../node_modules/react-native/android"
   -      código final:
   -         allprojects {
    repositories {
        mavenLocal()
        jcenter()
        maven {
            // All of React Native (JS, Obj-C sources, Android binaries) is installed from npm
            url "$rootDir/../node_modules/react-native/android"
        }
    }
}

He tenido que instalar y aceptar el t&c del platforms-tools 23 para que funcionara.
He tenido que instalar el JDK usando:
    - sudo apt-get install openjdk-8-jdk
    - export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64

Para que se deployara el apk he tenido que hacer:

    - export PATH="/home/daviz/Android/Sdk/platform-tools":$PATH
OJO a la mayúscula de Sdk

No sé pq pero para que se ejecute el index.android.js peta algo del bundle, hay que ejecutar este comando:
   - mkdir android/app/src/main/assets
   - react-native bundle --platform android --dev false --entry-file index.android.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res
   - para automatizar añadir al package.json este script:
   -      "android-linux": "react-native bundle --platform android --dev false --entry-file index.android.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res && react-native run-android" y ejecutar
   -      npm run android-linux

/bin/sh: 1: adb: not found
        - export PATH="/home/daviz/Android/Sdk/platform-tools":$PATH
OJO a la mayúscula de Sdk


links:
https://github.com/facebook/react-native/issues/11413
https://github.com/zo0r/react-native-push-notification/issues/260
https://stackoverflow.com/questions/44446523/unable-to-load-script-from-assets-index-android-bundle-on-windows
