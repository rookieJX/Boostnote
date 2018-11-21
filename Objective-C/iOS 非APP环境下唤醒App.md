### iOS 非APP环境下唤醒App

#### 1. 系统相关

|应用名称|URL Scheme|
|:--|:--|
|短信|sms://|
|app store|itms-apps://|
|电话|tel://|
|无线局域网|App-Prefs:root=WIFI|
|蓝牙|App-Prefs:root=Bluetooth|
|蜂窝移动网络|App-Prefs:root=MOBILE\_DATA\_SETTINGS_ID|
|个人热点|App-Prefs:root=INTERNET_TETHERING|
|运营商|App-Prefs:root=Carrier|
|通知|App-Prefs:root=NOTIFICATIONS_ID|
|通用|App-Prefs:root=General|
|通用-关于本机|App-Prefs:root=General&path=About|
|通用-键盘|App-Prefs:root=General&path=Keyboard|
|通用-辅助功能|App-Prefs:root=General&path=ACCESSIBILITY|
|通用-语言与地区|App-Prefs:root=General&path=INTERNATIONAL|
|通用-还原|App-Prefs:root=Reset|
|墙纸|App-Prefs:root=Wallpaper|
|Siri|App-Prefs:root=SIRI|
|隐私|App-Prefs:root=Privacy|
|Safari|App-Prefs:root=SAFARI|
|音乐|App-Prefs:root=MUSIC|
|音乐-均衡器|App-Prefs:root=MUSIC&path=com.apple.Music:EQ|
|照片与相机|App-Prefs:root=Photos|
|FaceTime|App-Prefs:root=FACETIME|

#### 2. 应用相关

|应用名称|URL Scheme|
|:--|:--|
|微博|weibo://|
|QQ|mqq://|
|QQ群组|mqqapi://card/show\_pslcard?src\_type=internal&version=1&card_type=group&uin={QQ群号}|
|QQ联系人|mqqapi://card/show\_pslcard?src\_type=internal&version=1&uin={QQ号码}|
|支付宝|alipay://|
|微信|weixin://|
|微信|wechat://|
|微信-扫一扫|weixin://dl/scan|
|微信-反馈|weixin://dl/feedback|
|微信-朋友圈|weixin://dl/moments|
|微信-设置|weixin://dl/settings|
|微信-消息通知设置|weixin://dl/notifications|
|微信-聊天设置|weixin://dl/chat|
|微信-通用设置|weixin://dl/general|
|微信-公众号|weixin://dl/officialaccounts|
|微信-游戏|weixin://dl/games|
|微信-帮助|weixin://dl/help|
|微信-个人信息|weixin://dl/profile|
|微信-功能插件|微信-功能插件|
|虾米音乐|xiami://|
|chrome|googlechrome://|
|微博国际版|weibointernational://|
|摩拜单车|mobike://|
|ofo|ofoapp://|
|有道云笔记|youdaonote://|
|印象笔记|evernote://|
|今日头条|snssdk141://|
|网易新闻|网易新闻|
|网易云音乐|orpheuswidget://|
|QQ音乐|qqmusic://|
|QQ音乐最近播放|qqmusic://today?mid=31&k1=2&k4=0|
|美团外卖|meituanwaimai://|
|美团|imeituan://|
|Gmail|googlegmail://|
|网易邮箱|neteasemail://|
|QQ邮箱|qqmail://|
|腾讯视频|tenvideo://|
|爱奇艺|iqiyi://|
|12306|cn.12306://|
|有道词典|yddict://|
|钉钉|dingtalk://|


#### 3. ```URL Schemes```

  由于苹果采用的特殊的方式防护用户数据安全，就是我们常说的沙盒方式。一个程序只能访问其特定指定的内存空间，对于其他空间是无法访问。这就造成了一个问题就是，如果我们想要通过一个程序A，来唤醒程序B,并且与B交互的话就很困难。好在我们有一个方式 通过 ```URL Schemes```.

 对于```URL Schemes```，很像我们一个网页的```URL```.我们可以这么比方。对于一个浏览器```Chrome```来说，一个个网站：百度，谷歌，淘宝，京东等。类比手机可以说 ```Chrome``` 就是我们的手机。百度，谷歌，等就是我们手机上一个个的应用程序。现在我们需要在应用程序之间相互唤醒。那么我们就需要 ```URL Schemes``` 来操作。
 
  例如 ```weixin://dl/moments```中```weixin```就是微信的```Scheme```。完全可以按照一个```URL```的方式来理解```Scheme```。
  
  **注意**
  
  - 所有的网页都有```url```,但不是所有的应用程序都有自己的```scheme```,更不是每个应用程序的功能都有```scheme```。
  - 一个网址只对应一个网页，但并非每个```URL Scheme```都只对应一款产品。因为苹果没有对```URL Scheme```不允许重复有硬性要求。
  - 一般网页的```URL```比较好预测。但是```iOS```上的```URL Scheme```是我们自己定义，没有统一标准，不好预测。


#### 4. 注册自定义 ```URL Scheme```

1. 在项目中 ```Xcode Project Navigator```中找到```info.plist```,点击添加```URL Types```.
2. 其中```URL Types```是一个数组，点击打开```Item 0```，继续点击打开 ```Item 0```为一个字典，点击打开其中有```URL identifier```一般设置其值为我们项目```Bundle ID```
3. 在打开的```Item 0```中点击继续添加，下拉选择```URL Schemes```,这里是一个数组，你可以定义多个。例如定义```Lee```。
> 这里定义```URL Schemes```是不需要```://```，只需要字符串就行。
> 
4. 定义好之后我们可以直接拿浏览器进行验证,输入```Lee://```

#### 5. 测试自定义 ```URL Scheme```

1. 新建工程B，创建按钮。打开工程A


```objc
NSString *url = @"Lee://";
if ([[UIApplication sharedApplication] canOpenURL:[NSURL URLWithString:url]]) {
    [[UIApplication sharedApplication] openURL:[NSURL URLWithString:url] options:@{} completionHandler:nil];
}else{
    NSLog(@"打不开");
}
```

> 可能会打不开，因为我们么有在工程B中没有添加 ```query schemes```
> 

2. 在工程B中添加 ```query schemes```

- 在B中打开 ```info.plist```
- 点击使用 ```Open As Source Code```方式打开
- 添加如下代码


```xml
<key>LSApplicationQueriesSchemes</key> 
  <array> 
  <string>zhunaer</string> 
  </array>
```

#### 6. 通过 ```URL Scheme```传值

B工程通过 ```URL Scheme``` 传值到A工程。可以通过类似于```URL```拼接参数一样的进行拼接。
例如：``` @"Lee://?name=xxx&age=22"``` 方式

**B工程完整代码：**

```objc
NSString *url = @"Lee://?name=xxx&age=22";
if ([[UIApplication sharedApplication] canOpenURL:[NSURL URLWithString:url]]) {
    [[UIApplication sharedApplication] openURL:[NSURL URLWithString:url] options:@{} completionHandler:nil];
}else{
    NSLog(@"打不开");
}
```

对于iOS新接口

```objc
[[UIApplication sharedApplication] openURL:URL options:@{} completionHandler:nil];
```

> 目前```options```可传入参数```Key```在```UIApplication```头文件只有一个:```UIApplicationOpenURLOptionUniversalLinksOnly```,其对应的```Value```为布尔值,默认为```False```.如该```Key```对应的```Value```为```True```,那么打开所传入的```Universal Link```时,只允许通过这个```Link```所代表的```iOS```应用跳转的方式打开这个链接,否则就会返回```success```为```false```,也就是说只有安装了```Link```所对应的```App```的情况下才能打开这个```Universal Link```,而不是通过启动```Safari```方式打开这个```Link```的代表的网站.


**A工程完成代码：**

```swift
func application(_ app: UIApplication, open url: URL, options: [UIApplication.OpenURLOptionsKey : Any] = [:]) -> Bool {
        NSLog("calling application bundle id: %@",options);
        NSLog("url shceme:\(url.scheme!)");
        NSLog("参数:\(url.query!)");
        return true
    }
    
 /**
    calling application bundle id: {
      UIApplicationOpenURLOptionsOpenInPlaceKey = 0;
      UIApplicationOpenURLOptionsSourceApplicationKey = "com.rookie.T";
    }
    url shceme:Lee
    参数:name=xxx&age=22
 */
```
    