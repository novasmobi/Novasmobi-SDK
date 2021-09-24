# iOS接入文档
1.导入和工程配置
SDK是使用OC编写的.framework动态库。

1.1将demo中RICHSDK.framework文件，GoogleService-Info.plist和AdjustStatistic.plist拖入工程。

1.2将这1个库设置为动态库，会默认在Linked Framework中也添加这1个库，如果Linked Framework已经存在，请删除重复的库。最后是下面这种样子。

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/1.png)

1.3.Build Setting中关闭bitcode，添加-ObjC

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/2.png)

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/3.png)

2、Info.plist文件配置
注意:下列所有配置请务必使用您实际的应用 ID，而不是截图列出的 ID。 否则将会导致崩溃。

可以参照给的参数和demo里面的配置来设置

（2.1）添加 http支持

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/4.png)

（2.2）添加 Facebook相关内容

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/5.png)

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/6.png)


![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/8.png)

（2.3）添加谷歌相关内容

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/9.png)

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/10.png)

（2.4）添加Line相关内容,开启Associated Domains权限

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/11.png)

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/12.png)

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/14.png)

（2.5）配置ATT权限和SKAdNetworkIdentifier

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/15.png)

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/16.png)

（2.6）添加ironSource_ID

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/13.png)

（2.7）推送配置
请参照 demo 中的工程配置 Capabilities,打开 Background Modes 中 Remote notifications 权限，Game Center，In-App Purchase，Sign in with Apple 和 Push Notifications 权限，如下图所示 

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/17.png)


3.SDK初始化与API接口

3.1 SDK初始化

在AppDelegate.m中添加头文件引用

#import <RICHSDK/RICHSDK.h>

- 在AppDelegate.m的didFinishLaunchingWithOptions方法中添加以下代码

```
//初始化SDK   app_id, deskey, googleSignInClientID这些参数需要联系游戏发行方获取，改为自己的！

[RICHSDK registerRICHSDKWithAppid:app_id appkey:deskey googleSignInClientID:googleSignInClientID application:application options:launchOptions result:^(BOOL isSuccess) {

}];
```

- 在AppDelegate.m中添加以下方法
```
- (BOOL)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray<id<UIUserActivityRestoring>> * _Nullable))restorationHandler
{
    [RICHSDK application:application continueUserActivity:userActivity restorationHandler:nil];
    return YES;
    // Your other code to handle universal links and/or user activities.
}

- (void)applicationDidBecomeActive:(UIApplication *)application {
    [RICHSDK applicationDidBecomeActive:application];
}

- (void)applicationDidEnterBackground:(UIApplication *)application{
    [RICHSDK appDidEnterBackground:application];
}

- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation {
    [RICHSDK application:application openURL:url sourceApplication:sourceApplication annotation:annotation];
    return YES;
}

- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo
fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler {

    [RICHSDK didReceiveRemoteNotification:userInfo];
    
    completionHandler(UIBackgroundFetchResultNewData);
    
}
```

3.2 登陆与回调

- SDK为游戏方提供了两种登录方式，即弹框登录和静默登录

- 在项目中需要进行登录操作的xxx.h或xxx.m文件中导入 #import <RICHSDK/RICHSDK.h>

```
//弹框登录

 [RICHSDK loginWithSuccess:^(NSDictionary * _Nonnull userInfo) {

    NSLog(@"弹框登录成功 ： %@",userInfo);
    
    } failed:^(NSString * _Nonnull result) {

    NSLog(@"弹框登录失败 ： %@",result);

 }];
```
```
//静默登录

[RICHSDK silenceLoginWithSuccess:^(NSDictionary * _Nonnull userInfo) {

    NSLog(@"静默登录成功 ： %@",userInfo);
    
} failed:^(NSString * _Nonnull result) {

    NSLog(@"静默登录失败 ： %@",result);
}];
```

3.3 同步角色与回调

- 在登录成功获取SDK用户信息之后，需要调用此方法，否则会影响后续的其他方法

- 在游戏使用中，此函数中的任意参数发生变化，都需要调用此函数，进行数据同步

- 角色上报节点 1.角色创建时   2.进去游戏时 3.角色升级时

```
// 同步游戏角色(游戏登录之后必须调用)
//@brief 角色信息上报，要求角色信息每次变更的时候调用（比如等级的提升）
//@param zoneID 角色区服id
//@param zoneName 角色区服
//@param roleID 角色id
//@param roleLevel 角色等级 NSInteger类型
//@param roleName 角色名称
[RICHSDK reportRoleInformationWithNewZoneID:@"" newZoneName:@"" newRoleID:@"" newRoleLevel:1 newRoleName:@""];
```

3.4 内购充值与回调

```
//@param vorderID 订单id
//@param zoneID 角色区服id
//@param zoneName 角色区服
//@param roleID 角色id
//@param roleLevel 角色等级
//@param roleName 角色名称
//@param appleproductID 苹果产品id 计费点（com.game.id）
//@param success block 支付成功返回的字符串，block里面处理支付成功的逻辑
//@param failed block 支付失败返回的字符串，block里面处理支付失败的逻辑
[RICHSDK payWithVorderID:vorderID zoneID:@"" zoneName:@"" roleID:@"" roleLevel:@"" roleName:@"" appleproductID:@""
    success:^(NSString *result) {
    NSLog(@"成功 ： %@",result);
}
failed:^(NSString *result) {
    NSLog(@"失败 ： %@",result);
}];
```

3.5 打开SDK账号中心界面

```
[RICHSDK bindingFacebookOrGameCenterWithSuccess:^(NSString * _Nonnull isBind) {

    NSLog(@"绑定第三方账号成功 ： %@",isBind);
    
} switchGameAccount:^(NSString * _Nonnull message) {

    NSLog(@"切换账号成功 ： %@",message);
    //切换账号后需跳转到游戏初始化界面  然后调用弹窗登录界面
    [RICHSDK loginWithSuccess:^(NSDictionary * _Nonnull userInfo) {
        NSLog(@"登录成功 ： %@",userInfo);
    } failed:^(NSString * _Nonnull message) {
        NSLog(@"登录失败 ： %@",message);
    }];
}];
```

3.6 打开SDK绑定第三方账号界面

```
[RICHSDK bindingThirdPartyAccountWithSuccess:^(NSString * _Nonnull isBind) {
    
}];
```

3.7 打开SDK客服界面
```
[RICHSDK onlineService];
```

3.8 获取GM有无新消息接口
```
  //获取GM有无新消息接口
 [RICHSDK registerGetNewNewsResult:^(BOOL isHave) {
        if (isHave) {
            [SVProgressHUD showSuccessWithStatus:@"有新消息"];
            NSLog(@"有新消息");
        }else{
            [SVProgressHUD showSuccessWithStatus:@"没有新消息"];
            NSLog(@"没有新消息");
        }
  }];
```


3.9 获取推送token

```
[RICHSDK getFcmToken:^(NSString * _Nonnull result) {

    NSLog(@"获取推送参数成功 ： %@",result);
    
}];
```

3.10  分享

注意：分享的链接必须为完整链接，示例："http://www.baidu.com/share.php?app_id=100000240&open_id=HY102560309&role_id=50100523000191"

客户端需要分享出去的URL后拼接三个参数: app_id, open_id, role_id, 
例:app_id=123&open_id=HY123&role_id=123, 需要分享的域名url由运营提供


```
//@brief 分享  图片和链接分享方式二选一  不需要的的参数传空
//@param shareImage 分享图片
//@param shareContentURL 分享链接
//@param shareHashtag 分享超话 可以随链接一起分享 示例@"#MadeWithHackbook"
//@param viewController 视图控制器 必传
//@param success block 处理分享成功的逻辑
//@param failed block 处理分享失败的逻辑
[RICHSDK fbShareImage:nil shareContentURL:nil shareHashtag:nil viewController:self success:^(NSString * _Nonnull result) {
    NSLog(@"分享成功回调%@",result);
} failed:^(NSString * _Nonnull result) {
    NSLog(@"分享失败回调%@",result);
}];
```

3.11  调用播放视频广告

注意：viewController参数必须传UIViewController类型


```
[RICHSDK rewardedVideoWithOpen:^(NSString * _Nonnull result) {
    NSLog(@"视频广告开始播放%@",result);
}viewController:self success:^(NSDictionary * _Nonnull rvPlacementInfo) {

    //此回调内可以给用户发放奖励
    NSLog(@"视频广告播放完毕回调%@",rvPlacementInfo);
    
} failed:^(NSString * _Nonnull result) {
    NSLog(@"视频广告失败回调%@",result);
}];
```

3.12  埋点事件

```
//@brief 自定义统计事件
//@param eventName 事件名称 可传常量ADJUST_C_P_1或者字符串"c1"，c为小写
//@param eventDic 事件参数字典
//@param useFB  如果传YES 则启用firebase和FB打点  传NO 则不启用firebase和FB打点
//下面2种方式都可以
[RICHSDK statistic_customEvent:ADJUST_C_P_1 withEventDic:nil useFB:YES];
```
```
[RICHSDK statistic_customEvent:@"c1" withEventDic:nil useFB:YES];
```
3.13  获取本地化金额接口

```
NSArray * productArr = @[@"com.game.id1",@"com.game.id2"];

[RICHSDK getLocalizedAmountWithProduct_idArray:productArr success:^(NSArray * _Nonnull userInfo) {

    NSLog(@"获取本地金额成功 ： %@",userInfo);

}failed:^(NSString * _Nonnull result) {

    NSLog(@"获取本地金额失败 ： %@",result);

}];
```

3.14  弹出系统评价接口

```
[RICHSDK evaluation];
```

3.15  获取用户绑定信息接口

```
[RICHSDK getAccountBindingListSuccess:^(NSDictionary * _Nonnull userInfo) {
        NSLog(@"获取用户绑定信息%@",userInfo);
    } failed:^(NSString * _Nonnull result) {
        
}];
```

3.16  查询用户邀请好友列表接口

```
//role_id 用户的role_id,必传参数，不能为空值
//success block 用户邀请的好友列表
//failed block 查询失败返回的字符串
[RICHSDK checkInviteListWithRole_id:@"123" success:^(NSDictionary * _Nonnull inviteListInfo) {
        
} failed:^(NSString * _Nonnull result) {
        
}];

success返回值示例：邀请了1个好友的情况
(
        {
        openid = 101743333;
        "reg_time" = 1574819767;
    }
)
```

   

