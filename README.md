### Test Project for the MtAdmob Plugin

With this Plugin you can add a Google Admob Ads inside your Xamarin Android and iOS Projects with a single line!!!
The plugin supports: Banners, Interstitial and Rewarded Videos

This is the test project, to show you how to use the plugin

I've copied here to guide to use the plugin:

### BANNER

To add a Banner on a page you have two options:

#### XAML

```csharp
<controls:AdView x:Name="myAds"></controls:AdView>
```

remember to add this line in your XAML:
```
xmlns:controls="clr-namespace:MarcTron.Plugin.Controls;assembly=Plugin.MtAdmob"
```

#### CODE
```
AdView ads = new AdView();
```

### PROPERTIES

For each AdView if you want, you can set these properties:
AdsId: To add the id of your ads
PersonalizedAds: You can set it to False if you want to use generic ads (for GDPR...) (It works only for Android Banners, for the others, you must ask for consent)

### GLOBAL PROPERTIES

AdsId: To add the id of your ads
PersonalizedAds: You can set it to False if you want to use generic ads (for GDPR...) (It works only for Android Banners, for the others, you must ask for consent)
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

Update your AndroidManifest.xml file by adding the 2 lines of code inside the application tag:
```
<manifest>
    <application>
        <meta-data android:name="com.google.android.gms.version" android:value="@integer/google_play_services_version" />
		    <activity android:name="com.google.android.gms.ads.AdActivity" android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" android:theme="@android:style/Theme.Translucent" />
    </application>
</manifest>
```

Before loading ads, have your app initialize the Mobile Ads SDK by calling MobileAds.initialize() with your AdMob App ID. 
This needs to be done only once, ideally at app launch. For example:

```csharp
protected override void OnCreate(Bundle savedInstanceState)
        {
            TabLayoutResource = Resource.Layout.Tabbar;
            ToolbarResource = Resource.Layout.Toolbar;

            base.OnCreate(savedInstanceState);
            MobileAds.Initialize(ApplicationContext, "xx-xxx-xxx-xxxxxxxxxxxxxxxx~xxxxxxxxxx");
            Xamarin.Forms.Forms.Init(this, savedInstanceState); 
            LoadApplication(new App());
        }
```



That's it. Cannot be easier than that :)


### LINKS

Available on Nuget: https://www.nuget.org/packages/MarcTron.Admob

Project website: https://www.xamarinexpert.it/Plugin/MTAdmob

Tutorial: https://www.xamarinexpert.it/blog/admob-made-easy/

Test Project: https://github.com/marcojak/TestMTAdmob/

To report any issue: https://bitbucket.org/marcojak81/mtadmob
