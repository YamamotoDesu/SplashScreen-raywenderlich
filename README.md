# [SplashScreen-raywenderlich](https://www.raywenderlich.com/32555180-splash-screen-tutorial-for-android)
Splash Screen Tutorial for Android

Fast forward to Android 12, which added the SplashScreen API. From Android 12 onward, all apps show a default splash screen, and developers can customize it according to their requirements.

# Creating a Simple Splash Screen
![2022-06-12 12 16 58](https://user-images.githubusercontent.com/47273077/173212757-c7b73d78-7a5f-40ed-ab85-230c4e0121fd.gif)

##  1. Adding the Dependency
### ■ SplashScreen API Dependency
build.gradle
```gradle
implementation 'androidx.core:core-splashscreen:1.0.0-beta01'
```

## 2. Adding the Adaptive Icon
### ■ SplashScreen API theme
styles.xml
```xml
<style name="Theme.App.Starting" parent="Theme.SplashScreen">
  <item name="windowSplashScreenAnimatedIcon">@drawable/ic_launcher_foreground</item>
  <item name="postSplashScreenTheme">@style/AppTheme</item>
  <item name="windowSplashScreenBackground">@color/ic_launcher_background</item>
</style>

```

### ■ Legacy Splash Screen Theme
```xml 
  <style name="LegacySplashTheme" parent="Theme.AppCompat.NoActionBar">
    <item name="android:windowBackground">@drawable/legacy_splash_background</item>
    <item name="android:windowTranslucentStatus">true</item>
    <item name="android:windowTranslucentNavigation">true</item>
  </style>
```

## 3. Setting the Style
### ■ SplashScreen API Setting
```xml
android:theme="@style/Theme.App.Starting"
```

Your file should look like this:
```xml
        <activity
            android:name=".MainActivity"
            android:exported="true"
            android:theme="@style/Theme.App.Starting">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
```

### ■ Legacy Splash Screen Setting
```xml
   <activity
      android:name=".LegacySplashActivity"
      android:theme="@style/LegacySplashTheme"
      android:exported="true">
      <!--
        launching Activity. Note: You will also need to comment out the equivalent intent-filter
        block of the MainActivity above.
      -->
      <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
      </intent-filter>
    </activity>
```

### 4. Installing the Splash Screen
MainActivity.kt
```kt
import androidx.core.splashscreen.SplashScreen.Companion.installSplashScreen

val splashScreen = installSplashScreen()
```

Your file should look like this:
```kt
  override fun onCreate(savedInstanceState: Bundle?) {

    // TODO: Install Splash Screen
    val splashScreen = installSplashScreen()

    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main)

    startLoadingContent()
```
