# Отправка событий о переходе по deeplink

Для ручной отправки события об открытии и переходе по deeplink необходимо вызвать следующий код:

{% tabs %}
{% tab title="Swift" %}
`TrackerTop100.trackDeeplink(link: deeplink)`
{% endtab %}

{% tab title="Objective-C" %}
`[TrackerTop100 trackDeeplinkWithLink: deeplink]`
{% endtab %}
{% endtabs %}

**DEEPLINK (обязательный) - строковое представление deeplink, например, "myapp://path/to/screen"**



{% tabs %}
{% tab title="Swift" %}
```
func application(  
     _ app: UIApplication,  
     open url: URL,  
     options: [UIApplication.OpenURLOptionsKey: Any] = [:]  
 ) -> Bool {  
     TrackerTop100.trackDeeplink(link: url.absoluteString)  
     return true  
 }  
  
 func application(  
     _ application: UIApplication,  
     continue userActivity: NSUserActivity,  
     restorationHandler: @escaping (\[UIUserActivityRestoring\]?) -> Void  
 ) -> Bool {  
     if userActivity.activityType == NSUserActivityTypeBrowsingWeb,  
        let webpageURL = userActivity.webpageURL  
     {  
         TrackerTop100.trackDeeplink(link: webpageURL.absoluteString)  
     }  
     return true  
 }
```

<figure><img src="../../../.gitbook/assets/Снимок экрана 2024-02-08 в 15.48.16.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Objective-C" %}
```
@implementation AppDelegate  
  
- (BOOL)application:(UIApplication *)app openURL:(NSURL *)url  
    options:(NSDictionary<UIApplicationOpenURLOptionsKey,id> *)options  
{  
    [TrackerTop100 trackDeeplinkWithLink: url.absoluteString\];  
    return YES;  
}  
  
- (BOOL)application:(UIApplication *)application  
    continueUserActivity:(NSUserActivity *)userActivity  
    restorationHandler:(void (^)(NSArray<id<UIUserActivityRestoring>> * _Nullable))restorationHandler  
{  
    if ([userActivity.activityType isEqualToString:NSUserActivityTypeBrowsingWeb]) {  
        [TrackerTop100 trackDeeplinkWithLink: userActivity.webpageURL.absoluteString];  
    }  
    return YES;  
}  
  
@end
```

<figure><img src="../../../.gitbook/assets/Снимок экрана 2024-02-08 в 15.48.56 (1).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}
