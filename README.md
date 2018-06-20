# AndroidPlugin


* 開啟 Android 專案
* 匯入 Unity Java classes
* 編寫 native Java code
* 處理 build.gradle
* 編譯 .jar 
* unity 中加入.jar
* 編寫 unity Manifest.xml
* 編寫 C# Script



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
[開發 Unity Android Plugin – 從零開始]https://douduck08.wordpress.com/2016/06/08/birth-of-unity-android-plugin/
