# iOS接入文档   

服务端文档地址http://doc.mobinovas.com:10030/web/#/80?page_id=1347

1.导入和工程配置
SDK是使用OC编写的.framework动态库。

1.1将demo中DGTRSDK.framework和VKSdkFramework文件，GoogleService-Info.plist和AdjustStatistic.plist拖入工程。

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

（2.2）添加 Facebook、Google和VK相关内容

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/5.png)

![Image text](https://github.com/novasmobi/Novasmobi-SDK/blob/main/iOS/img/6.png)


![Image text](https://github.com/novasmobi/Novasmobi-SDK/blob/main/iOS/img/8.png)


（2.5）配置ATT权限和SKAdNetworkIdentifier

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/15.png)

将 以下 SKAdNetwork ID 添加到您应用的 Info.plist 以启用转化跟踪，共计93个


	<key>SKAdNetworkItems</key>
	<array>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>2fnua5tdw4.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>2u9pt9hc89.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>3qcr597p9d.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>3qy4746246.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>3sh42y64q3.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>424m5254lk.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>4468km3ulz.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>4dzt52r2t5.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>4fzdc2evr5.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>578prtvx9j.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>5a6flpkh64.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>7ug5zh24hu.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>8c4e2ghe7u.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>8s468mfl3y.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>9rd848q2bz.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>9t245vhmpl.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>av6w8kgt66.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>c6k4g5qg8m.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>cstr6suwn9.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>e5fvkxwrpn.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>f38h382jlk.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>hs6bdukanm.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>kbd757ywx3.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>klf5c3l5u5.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>n6fk4nfna4.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>p78axxw29g.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>ppxm28t8ap.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>prcb7njmu6.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>s39g8k73mm.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>t38b2kh725.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>uw77j35x4d.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>v4nxqhlyqp.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>v72qych5uu.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>wzmmz9fp6w.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>yclnxrl5pm.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>ydx93a7ass.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>zq492l623r.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>24t9a8vw3c.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>275upjj5gd.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>294l99pt4k.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>32z4fx6l9h.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>3rd42ekr43.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>4pfyvq9l8r.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>523jb4fst2.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>54nzkqm89y.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>5l3tpt7t6e.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>5lm9lj6jb7.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>6xzpu9s2p8.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>79pbpufp6p.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>7rz58n8ntl.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>9b89h5y424.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>9nlqeag3gk.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>c3frkrj4fj.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>cg4yq2srnc.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>cj5566h2ga.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>ejvt5qm6ak.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>feyaarzu9v.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>g28c52eehv.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>ggvn48r87g.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>glqzh8vgby.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>gta9lk7p23.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>k674qkevps.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>kbmxgpxpgc.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>ludvb6z3bs.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>m8dbw4sv7c.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>mlmmfzh3r3.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>mtkv5xtk9e.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>n9x2a789qt.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>pwa73g5rt2.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>qqp299437r.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>r45fhb6rf7.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>rvh3l7un93.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>tl55sbb4fm.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>wg4vff78zm.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>x8jxxk4ff5.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>xy9t38ct57.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>zmvfpc5aq8.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>n38lu8286q.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>v9wttpbfk9.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>su67r6k2v3.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>44jx6755aq.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>737z793b9f.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>w9q455wk68.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>22mmun2rn5.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>238da6jt44.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>488r3q3dtq.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>5tjdwbrq8w.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>f73kdq92p3.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>f7s53z58qe.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>lr83yxwka7.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>mp6xlyr22a.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>v79kvwwj4g.skadnetwork</string>
        </dict>
        <dict>
            <key>SKAdNetworkIdentifier</key>
            <string>x44k69ngh6.skadnetwork</string>
        </dict>
	</array>

请更新您的 Info.plist 以显示访问 IDFA 的 App Tracking Transparency 授权请求。添加 NSUserTrackingUsageDescription 键。

下面是一个示例描述文本：

<key>NSUserTrackingUsageDescription</key>
<string>This identifier will be used to deliver personalized ads to you</string>

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/16.png)


（2.7）推送配置
请参照 demo 中的工程配置 Capabilities,打开 Background Modes 中 Remote notifications 权限，Game Center，In-App Purchase，Sign in with Apple 和 Push Notifications 权限，如下图所示 

![Image text](https://raw.githubusercontent.com/zqkzhang/Novasmobi-SDK/main/iOS/img/17.png)


3.SDK初始化与API接口

3.1 SDK初始化

在AppDelegate.m中添加头文件引用

#import <DGTRSDK/DGTRSDK.h>

- 在AppDelegate.m的didFinishLaunchingWithOptions方法中添加以下代码

```
//初始化SDK   app_id, deskey, googleSignInClientID这些参数需要联系游戏发行方获取，改为自己的！

[DGTRSDK registerDGTRSDKWithAppid:app_id appkey:deskey googleSignInClientID:googleSignInClientID application:application options:launchOptions result:^(BOOL isSuccess) {

}];
```

- 在AppDelegate.m中添加以下方法  以下方法为必须添加的
```
- (BOOL)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray<id<UIUserActivityRestoring>> * _Nullable))restorationHandler
{
    [DGTRSDK application:application continueUserActivity:userActivity restorationHandler:nil];
    return YES;
    // Your other code to handle universal links and/or user activities.
}

- (void)applicationDidBecomeActive:(UIApplication *)application {
    [DGTRSDK applicationDidBecomeActive:application];
}

- (void)applicationDidEnterBackground:(UIApplication *)application{
    [DGTRSDK appDidEnterBackground:application];
}

- (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<UIApplicationOpenURLOptionsKey, id> *)options{
    [DGTRSDK application:app openURL:url options:options];
    return YES;
}

- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo
fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler {

    [DGTRSDK didReceiveRemoteNotification:userInfo];
    
    completionHandler(UIBackgroundFetchResultNewData);
    
}
```

3.2 登陆与回调

- SDK为游戏方提供了两种登录方式，即弹框登录和静默登录

- 在项目中需要进行登录操作的xxx.h或xxx.m文件中导入 #import <DGTRSDK/DGTRSDK.h>

```
//弹框登录

 [DGTRSDK loginWithSuccess:^(NSDictionary * _Nonnull userInfo) {

    NSLog(@"弹框登录成功 ： %@",userInfo);
    
    } failed:^(NSString * _Nonnull result) {

    NSLog(@"弹框登录失败 ： %@",result);

 }];
```
```
//静默登录

[DGTRSDK silenceLoginWithSuccess:^(NSDictionary * _Nonnull userInfo) {

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
[DGTRSDK reportRoleInformationWithNewZoneID:@"" newZoneName:@"" newRoleID:@"" newRoleLevel:1 newRoleName:@""];
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
[DGTRSDK payWithVorderID:vorderID zoneID:@"" zoneName:@"" roleID:@"" roleLevel:@"" roleName:@"" appleproductID:@""
    success:^(NSString *result) {
    NSLog(@"成功 ： %@",result);
}
failed:^(NSString *result) {
    NSLog(@"失败 ： %@",result);
}];
```

3.5 打开SDK账号中心界面

```
[DGTRSDK bindingFacebookOrGameCenterWithSuccess:^(NSString * _Nonnull isBind) {

    NSLog(@"绑定第三方账号成功 ： %@",isBind);
    
} switchGameAccount:^(NSString * _Nonnull message) {

    NSLog(@"切换账号成功 ： %@",message);
    //切换账号后需跳转到游戏初始化界面  然后调用弹窗登录界面
    [DGTRSDK loginWithSuccess:^(NSDictionary * _Nonnull userInfo) {
        NSLog(@"登录成功 ： %@",userInfo);
    } failed:^(NSString * _Nonnull message) {
        NSLog(@"登录失败 ： %@",message);
    }];
}];
```

3.6 打开SDK绑定第三方账号界面

```
[DGTRSDK bindingThirdPartyAccountWithSuccess:^(NSString * _Nonnull isBind) {
    
}];
```

3.7 打开SDK客服界面
```
[DGTRSDK onlineService];
```

3.8 获取GM有无新消息接口
```
  //获取GM有无新消息接口
  注意：登录成功后调用这个接口，后续只要有新消息就会回调这个接口。调用一次，会一直回调。
 [DGTRSDK registerGetNewNewsResult:^(BOOL isHave) {
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
[DGTRSDK getFcmToken:^(NSString * _Nonnull result) {

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
[DGTRSDK fbShareImage:nil shareContentURL:nil shareHashtag:nil viewController:self success:^(NSString * _Nonnull result) {
    NSLog(@"分享成功回调%@",result);
} failed:^(NSString * _Nonnull result) {
    NSLog(@"分享失败回调%@",result);
}];
```

3.11  调用播放视频广告

注意：viewController参数必须传UIViewController类型


```
[DGTRSDK rewardedVideoWithOpen:^(NSString * _Nonnull result) {
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
[DGTRSDK statistic_customEvent:ADJUST_C_P_1 withEventDic:nil useFB:YES];
```
```
[DGTRSDK statistic_customEvent:@"c1" withEventDic:nil useFB:YES];
```
3.13  获取本地化金额接口

```
NSArray * productArr = @[@"com.game.id1",@"com.game.id2"];

[JHDHSDK getLocalizedAmountWithProduct_idArray:productArr success:^(NSArray * _Nonnull userInfo) {

    NSLog(@"获取本地金额成功 ： %@",userInfo);

}failed:^(NSString * _Nonnull result) {

    NSLog(@"获取本地金额失败 ： %@",result);

}];
```

3.14  弹出系统评价接口

```
[JHDHSDK evaluation];
```

3.15  获取用户绑定信息接口

```
[DGTRSDK getAccountBindingListSuccess:^(NSDictionary * _Nonnull userInfo) {
        NSLog(@"获取用户绑定信息%@",userInfo);
    } failed:^(NSString * _Nonnull result) {
        
}];
```

3.16  查询用户邀请好友列表接口

```
//role_id 用户的role_id,必传参数，不能为空值
//success block 用户邀请的好友列表
//failed block 查询失败返回的字符串
[DGTRSDK checkInviteListWithRole_id:@"123" success:^(NSDictionary * _Nonnull inviteListInfo) {
        
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

   

