### Test Project for the MtAdmob Plugin

With this Plugin you can add a Google Admob Ads inside your Xamarin Android and iOS Projects with a single line!!!
This plugin supports: Banners, Interstitial and Rewarded Videos

### Release Notes
**Version 1.3**
 Fixed crash on iOS with multiple Banner
Improved code
 **To avoid compatibilty now the Banner control has been renamed from AdView to MTAdView**
 
**Version 1.2**
 With this version Loading and Showing Interstitials and rewarded videos are 2 separate events. Now the methods are:
  * void LoadInterstitial(string adUnit);
  * void ShowInterstitial();
  * bool IsInterstitialLoaded();
  * void LoadRewardedVideo(string adUnit);
  * void ShowRewardedVideo();
  * bool IsRewardedVideoLoaded();

  I've removed the two methods:
  * void ShowInterstitial(string adUnit);
  * void ShowRewardedVideo(string adUnit);

  Now you have to load the Interstitial or Rewarded Video and when you want you can show it. You can see if an interstitial or rewared video are loaded using the new methods
  * bool IsInterstitialLoaded();
  * bool IsRewardedVideoLoaded();

  Thanks to these changes you have now more control over the Ads.

**Version 1.1**
* Added support for Rewarded Videos
* Added events for Rewarded Videos
* Added events for Interstitials

**Version 1.0**
* Banner and Insterstitial for Android
* Banner and Insterstitial for iOS

### BANNER

To add a Banner on a page you have two options:

#### XAML

```csharp
<controls:MTAdView x:Name="myAds"></controls:MTAdView>
```

remember to add this line in your XAML:
```
xmlns:controls="clr-namespace:MarcTron.Plugin.Controls;assembly=Plugin.MtAdmob"
```

#### CODE
```
MTAdView ads = new MTAdView();
```

### IMPORTANT

To test the banner during the development google uses two Banner Id, one for Android and the other for iOS. Use them then remember to replace them with your own IDs:
```
Android: ca-app-pub-3940256099942544/6300978111
iOS: ca-app-pub-3940256099942544/2934735716
```

**If the Banners don't appear in your app, probably it's a size problem. To solve it, add this style you your app.xaml:**
```
<Style TargetType="controls:MTAdView">
    <Setter Property="HeightRequest">
        <Setter.Value>
            <x:OnIdiom Phone="50" Tablet="90"></x:OnIdiom>
        </Setter.Value>
    </Setter>
</Style>
```

### PROPERTIES

For each AdView if you want, you can set these properties:
AdsId: To add the id of your ads

PersonalizedAds: You can set it to False if you want to use generic ads (for GDPR...) (It works only for Android Banners, for the others, you must ask for consent)

**For GDPR it's better to rely on a custom consent instead or using the non personalized ads as I cannot guarantee it works. So it's better if you create a custom consent**

### GLOBAL PROPERTIES

AdsId: To add the id of your ads

PersonalizedAds: You can set it to False if you want to use generic ads (for GDPR...) (It works only for Android Banners, for the others, you must ask for consent)
**For GDPR it's better to rely on a custom consent instead or using the non personalized ads as I cannot guarantee it works. So it's better if you create a custom consent**

TestDevices: You can add here the ID of your test devices

You can use Global Properties in this way:
CrossMTAdmob.Current.UserPersonalizedAds = true;


### INTERSTITIAL

You can show an interstitial with a single line of code:

CrossMTAdmob.Current.ShowInterstitial();

To Load an interstitial you can use this line:

CrossMTAdmob.Current.LoadInterstitial("xx-xxx-xxx-xxxxxxxxxxxxxxxxx/xxxxxxxxxx");


### REWARDED VIDEO

You can show a Rewarded video with a single line of code:

CrossMTAdmob.Current.ShowRewardedVideo();

To Load a Rewarded Video you can use this line:

CrossMTAdmob.Current.LoadRewardedVideo("xx-xxx-xxx-xxxxxxxxxxxxxxxxx/xxxxxxxxxx");


### EVENTS FOR BANNERS

Just in case you need, the Banner ads offer 4 events:
```
AdsClicked		    When a user clicks on the ads
AdsClosed		    When the user closes the ads
AdsImpression	    Called when an impression is recorded for an ad.
AdsOpened		    When the ads is opened
```

### EVENTS FOR INTERSTITIALS

the Interstitial ads offer 3 events:
```
OnInterstitialLoaded        When it's loaded
OnInterstitialOpened        When it's opened      
OnInterstitialClosed        When it's closed
```

### EVENTS FOR REWARDED VIDEOS

The Rewarded Videos offer 7 events:
```
OnRewarded                          When the user gets a reward
OnRewardedVideoAdClosed             When the ads is closed
OnRewardedVideoAdFailedToLoad       When the ads fails to load
OnRewardedVideoAdLeftApplication    When the users leaves the application
OnRewardedVideoAdLoaded             When the ads is loaded
OnRewardedVideoAdOpened             When the ads is opened
OnRewardedVideoStarted              When the ads starts
```

### IMPORTANT

Remember to include the MTAdmob library with this code (usually it's added automatically):
```
using MarcTron.Plugin;
```


### IMPORTANT FOR ANDROID:

Before loading ads, have your app initialize the Mobile Ads SDK by calling MobileAds.initialize() with your AdMob App ID. 
This needs to be done only once, ideally at app launch. For example:

```csharp
protected override void OnCreate(Bundle savedInstanceState)
        {
            TabLayoutResource = Resource.Layout.Tabbar;
            ToolbarResource = Resource.Layout.Toolbar;

            base.OnCreate(savedInstanceState);
            <!-- Sample AdMob App ID: ca-app-pub-3940256099942544~3347511713 -->
            MobileAds.Initialize(ApplicationContext, "xx-xxx-xxx-xxxxxxxxxxxxxxxx~xxxxxxxxxx");
            Xamarin.Forms.Forms.Init(this, savedInstanceState); 
            LoadApplication(new App());
        }
```

### IMPORTANT FOR IOS:

Before loading ads, have your app initialize the Mobile Ads SDK by calling MobileAds.initialize() with your AdMob App ID. 
This needs to be done only once, ideally at app launch. For example:

```csharp
public override bool FinishedLaunching(UIApplication app, NSDictionary options)
        {
            global::Xamarin.Forms.Forms.Init();
            <!-- Sample AdMob App ID: ca-app-pub-3940256099942544~1458002511 -->
            MobileAds.Configure("xx-xxx-xxx-xxxxxxxxxxxxxxxx~xxxxxxxxxx");

            LoadApplication(new App());

            return base.FinishedLaunching(app, options);
        }
```

**In case the plugin doesn't install automatically the nuget package 
```
Xamarin.Google.iOS.MobileAds
```
you need to add it manually.**


That's it. Cannot be easier than that :)


### LINKS

Available on Nuget: https://www.nuget.org/packages/MarcTron.Admob

Project website: https://www.xamarinexpert.it/site/Plugin/MTAdmob

Tutorial: https://www.xamarinexpert.it/admob-made-easy/

To report any issue: https://bitbucket.org/marcojak81/mtadmob
