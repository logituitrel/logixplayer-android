# LOGIXPLAYER SDK(Android) #

## Overview ##
The LogixPlayer SDK provides easy and seamless integration for playing videos in an android app, also providing methods for customizing player UI and behaviour as per requirements.
LogixPlayer also supports easy integration with features such as DRM, IMA ads etc.,
and also provides event callbacks to the app.
LogixPlayer can also support multiple types of media sources and stereo modes.


*Logixplayer SDK documentation can be found at*: 

<https://github.com/logituitrel/logixplayer-android/blob/master/com/logituit/logixplayer-android/1.1.0/docs_1.1.0.zip>

Please always refer to the documentation corresponding to the player version used


## Including Logixplayer in your Android Project: ##

In your app's build.gradle file:

* Add the following code in repositories:

```repositories {
maven {
	url 'https://raw.github.com/logituitrel/logixplayer-android/master'
	}
}
```	

* In dependencies, add:

```
api ('com.logituit:logixplayer-android:0.8.4.1') {
        exclude  group:'com.google.android.gms'
}
```

Replace the player sdk version with the version used


## USING LOGIXPLAYER: ##


* Firstly, you will need to add LogixPlayerView into your xml file where you want your video to be played.
```
<com.logituit.logixsdk.logixplayer.ui.LogixPlayerView
    android:id="@+id/player_view"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"/>
```


* Second, you will need an ArrayList of one or more LogixPlayerEventListeners, which will notify you of player events.

```
public class PlayerActivity extends AppCompatActivity
        implements LogixPlayerEventListener, {
ArrayList<LogixPlayerEventListener> logixPlayerEventListeners = new ArrayList<>();
logixPlayerEventListeners.add(this);
}
```

* Thirdly, you need to construct a LogixPlayerImpl object by passing your context, LogixPlayerView, LogixPlayerEventListener, and LogixAdEventListener(if you also want to play ads through logix sdk, null if you don't).

```
LogixPlayerImpl logixPlayerImpl = new LogixPlayerImpl(this, logixPlayerView, logixPlayerEventListeners, this);
```

* Lastly, create a LogixPlayerImpl.LogixPlayerBuilder object using an Array of Uris that you want to play(and add any customizations), and call logixPlayerImpl.Initialize(logixPlayerBuilder).

```
LogixPlayerImpl.LogixPlayerBuilder logixPlayerBuilder;

    logixPlayerBuilder = new LogixPlayerImpl.LogixPlayerBuilder(uris)
            .autoPlay(true)
            .startWindow(startWindow)
            .startPosition(startPosition)
            .abrAlgorithm(abrAlgorithm)
            .preferExtensionDecoders(preferExtensionDecoders)
            .adUrl(adTagUrl)
            .subtitleUrl(subtitleUrl)
            .imaSdkSettings(imaSdkSettings)
            .mCompanionViewGroup(companionAdContainer);
```


## LISTENING TO LOGIXPLAYER EVENTS: ##
Override the interface methods of LogixPlayerEventListener which you have implemented in your player class.

```
public class PlayerActivity extends AppCompatActivity
        implements LogixPlayerEventListener, {
```


## HOW TO PASS DRM URL: ##

Before initializing logixplayer, set the drm session for the logixplayer:
```
logixPlayerImpl.setDrmSessionManager(drmLicenseUrl, drmScheme);
```


## RELEASING LOGIXPLAYER: ##
```
private void releasePlayer() {
    if (logixPlayerImpl != null) {
	logixPlayerImpl.releasePlayer();    
	}
}
```

## SELECTING VIDEO TRACKS: ##
You can get the list of available tracks from logixplayer:

```
logixPlayerImpl.getBitrates()
```

This will return a list of *VideoResolution* objects.
You can pass back the desired resolution into logixplayer as:

```
logixPlayerImpl.setBitrate(videoResolution);
```


## SELECTING AUDIO TRACKS: ##

You can get the list of available audio tracks from logixplayer:

```
logixPlayerImpl.getAudioTracks()
```

This will return a list of *AudioTrack* objects.
You can pass back the desired track into logixplayer as:

```
logixPlayerImpl.setAudioTrack(audioTrack);
```







