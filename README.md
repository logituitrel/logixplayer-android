LOGIXPLAYER SDK(Android)

Overview
The LogixPlayer SDK provides easy and seamless integration for playing videos in an android app, also providing methods for customizing player UI and behaviour as per requirements.
LogixPlayer also supports easy integration with features such as DRM, IMA ads etc.,
and also provides event callbacks to the app.
LogixPlayer can also support multiple types of media sources and stereo modes.

Logixplayer SDK documentation can be found at: https://github.com/logituitrel/logixplayer-android/blob/master/com/logituit/logixplayer-android/1.1.0/docs_1.1.0.zip


Including Logixplayer in your Android Project:
In your app's build.gradle file:
Add the following code in repositories:
repositories {
	    maven {
	    url 'https://raw.github.com/logituitrel/logixplayer-android/master'
	    }
	}	
In dependencies, add:
api ('com.logituit:logixplayer-android:0.8.4.1') {
        exclude  group:'com.google.android.gms'
    	}



USING LOGIXPLAYER:
Firtly, you will need to add LogixPlayerView into your xml file where you want your video to be played.
Second, you will need an ArrayList of one or more LogixPlayerEventListeners, which will notify you of player events.
Thirdly, you need to construct a LogixPlayerImpl object by passing your context, LogixPlayerView, LogixPlayerEventListener, and LogixAdEventListener(if you also want to play ads through logix sdk, null if you don't).
Lastly, create a LogixPlayerImpl.LogixPlayerBuilder object using an Array of Uris that you want to play(and add any customizations), and call logixPlayerImpl.Initialize(logixPlayerBuilder).
