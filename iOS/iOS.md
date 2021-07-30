# iOS接入文档
1.导入和工程配置
SDK是使用OC编写的.framework动态库。
1.1将demo中KWMJSDK.framework文件，GoogleService-Info.plist和AdjustStatistic.plist拖入工程。
1.2将这1个库设置为动态库，会默认在Linked Framework中也添加这1个库，如果Linked Framework已经存在，请删除重复的库。最后是下面这种样子。
![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/1.png)

1.3.Build Setting中关闭bitcode，添加-ObjC
![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/2.png)
![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/3.png)
2、Info.plist文件配置
注意:下列所有配置请务必使用您实际的应用 ID，而不是截图列出的 ID。 否则将会导致崩溃。
（2.1）添加 http支持

（2.2）添加 Facebook相关内容

（2.3）添加谷歌相关内容

（2.4）添加Line相关内容,开启Associated Domains权限

（2.5）配置ATT权限和SKAdNetworkIdentifier

（2.6）添加ironSource_ID

（2.7）推送配置
请参照 demo 中的工程配置 Capabilities,打开 Background Modes 中 Remote notifications 权限，Game Center，In-App Purchase，Sign in with Apple 和 Push Notifications 权限，如下图所示 

3.SDK初始化与API接口
3.1 SDK初始化
在AppDelegate.m中添加头文件引用
#import <DKGASDK/DKGASDK.h>
- 在AppDelegate.m的didFinishLaunchingWithOptions方法中添加以下代码
//初始化SDK
//app_id, deskey, googleSignInClientID这些参数需要联系游戏发行方获取，改为自己的！

[DKGASDK registerDKGASDKWithAppid:app_id appkey:deskey googleSignInClientID:googleSignInClientID application:application options:launchOptions result:^(BOOL isSuccess) {
    NSLog(@"初始化成功");
 
    [DKGASDK silenceLoginWithSuccess:^(NSDictionary * _Nonnull userInfo) {
        NSLog(@"1静默登录成功 ： %@",userInfo);
        // 上报角色
        [DKGASDK reportRoleInformationWithNewZoneID:@"123123"
                                      newZoneName:@"天下"
                                        newRoleID:@"12345"
                                     newRoleLevel:132
                                      newRoleName:@"呼呼"];
    } failed:^(NSString * _Nonnull result) {
        NSLog(@"静默登录失败 ： %@",result);
    }];
}];

- 在AppDelegate.m中添加以下方法
- (BOOL)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray<id<UIUserActivityRestoring>> * _Nullable))restorationHandler
{
    [DKGASDK application:application continueUserActivity:userActivity restorationHandler:nil];
    return YES;
    // Your other code to handle universal links and/or user activities.
}

- (void)applicationDidBecomeActive:(UIApplication *)application {
    [DKGASDK applicationDidBecomeActive:application];
}
- (void)applicationDidEnterBackground:(UIApplication *)application{
    [DKGASDK appDidEnterBackground:application];
}

- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation {
    [DKGASDK application:application openURL:url sourceApplication:sourceApplication annotation:annotation];
    return YES;
}
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo
fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler {
    [DKGASDK didReceiveRemoteNotification:userInfo];
    completionHandler(UIBackgroundFetchResultNewData);
}

