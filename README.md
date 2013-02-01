# ShareKit
目前支持 `Weibo SDK` 和 `WeChat SDK`

## 如何使用

1. 启动的时候
```
ShareKit *share = [ShareKit sharedInstance];
// sinaweibo
[share sinaWeiboSetupWithAppKey:kSinaWeiboAppKey
                      appSecret:kSinaWeiboAppSecret
                 appRedirectURI:kSinaWeiboAppRedirectURI
              ssoCallbackScheme:kSinaWeiboScheme];
// wechat 
[share weChatSetupWithAppKey:kWeChatAppID];
```

2. 接管URL
```
- (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url {
    return [[ShareKit sharedInstance] handleOpenURL:url];
}

- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation {
    return [[ShareKit sharedInstance] handleOpenURL:url];
}
```

3. 在相关的需要分享的地方
```
ShareKit *share = [ShareKit sharedInstance];
[share sinaWeiboSendWithText:content
                   imageData:imageData
              authCompletion:^(NSError *error) {}
                     success:^{}
                     failure:^(NSError *error) {}]
```

更多请参考 `ShareKit.m`
