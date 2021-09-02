# Admob Native Ad Templates
A library to quickly implement admob native ad layouts in your android app.


## Installation

Add this to dependencies 
```groovy
implementation 'com.github.kamaravichow:admob-templates-android:1+'
```
- Latest version : [![](https://jitpack.io/v/kamaravichow/admob-templates-android.svg)](https://jitpack.io/#kamaravichow/admob-templates-android)

Don't forget to add this to project level gradle
```groovy
allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
```

## Usage 

Here are the simple implementations with this library

- First, you need to include the template as part of your layout.

```xml
<com.google.android.ads.nativetemplates.TemplateView
     android:id="@+id/ad_template_view"
     android:layout_width="match_parent"
     android:layout_height="wrap_content"
     app:gnt_template_type="@layout/gnt_custom_aravi_small" />
```

- Next, you need to give your template your native ad when it loads:

```java
AdLoader adLoader = new AdLoader.Builder(this, "ca-app-pub-3940256099942544/2247696110")
    .forNativeAd(new NativeAd.OnNativeAdLoadedListener() {
        @Override
        public void onNativeAdLoaded(NativeAd nativeAd) {
            NativeTemplateStyle styles = new
              NativeTemplateStyle.Builder().withMainBackgroundColor(background).build();
            TemplateView template = findViewById(R.id.my_template);
            template.setStyles(styles);
            template.setNativeAd(nativeAd);
        }
     })
     .build();

adLoader.loadAd(new AdRequest.Builder().build());
```

Learn more advanced customisations - [Native Templates for Admob](https://developers.google.com/admob/android/native/templates)

## Credits

This library is just a wrapper with a few custom and updated layouts. Basically a fork of [Google - Admob Templates](https://github.com/googleads/googleads-mobile-android-native-templates) 

## License

Copyright [2021] @google

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
