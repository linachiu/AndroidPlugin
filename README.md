# AndroidPlugin 備忘錄


* 開啟 Android 專案
* 匯入 Unity Java classes
* 編寫 native Java code
* 處理 build.gradle
* 編譯 .jar 
* unity 中加入.jar
* 編寫 unity Manifest.xml
* 編寫 C# Script


## 開啟 Android 專案
  很一般的開啟新專案

## 匯入 Unity Java classes
```
  位置：應用程式/unity/PlaybackEngines/AndroidPlayer/Viariations/{backend}/{buildType}/Classes/classes.jar
```
* 回到 android studio，在 ($projname) > app > libs 下貼上
* 在 classes.jar 上按下滑鼠右鍵，選擇 Add As Library...
 build.gradle 裡會出現 implementation files('libs/classes.jar')
就可以使用 ```import com.unity3d.player.UnityPlayer;``` 摟～

## 處理 build.gradle
* 将apply plugin: ‘com.android.application’，改成apply plugin: ‘com.android.library’
* 删除applicationId
* 在最後加入
```
task deleteOldJar(type: Delete) {
    delete 'release/mylib.jar'
}

// 匯出 jar 檔
task exportJar(type: Copy) {
    from('build/intermediates/bundles/release/')
    into('release/')
    include('classes.jar')
    // 將匯出的 jar 檔重新命名
    rename('classes.jar', 'mylib.jar')
}
exportJar.dependsOn(deleteOldJar, build)
```

* findview
```
  mWebView = (WebView) findViewById(context.getResources().getIdentifier("webView", "id", context.getPackageName()));
```

* activity & context
```
    final Activity a = UnityPlayer.currentActivity; //if unity
    final Context context = UnityPlayer.currentActivity; //if unity
```





## 參考資料
* [開發 Unity Android Plugin – 從零開始](https://douduck08.wordpress.com/2016/06/08/birth-of-unity-android-plugin/)
* [Android Studio 匯出 JAR 檔 - 加入 Unity classes.jar](http://gn02214231.pixnet.net/blog/post/178505239)
* [Unity Android Plugin 开发教程](https://rolyyu.github.io/2017/07/28/Unity-Android-Plugin-%E5%BC%80%E5%8F%91%E6%95%99%E7%A8%8B/)

