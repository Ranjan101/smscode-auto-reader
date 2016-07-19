# smscode-auto-reader

[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-smscode--auto--reader-green.svg?style=true)](https://android-arsenal.com/details/1/3947)

Help you to read sms code automatically.
## How to User

###1. Include SMS read permission

add`<uses-permission android:name="android.permission.READ_SMS" />` in your AndroidManifest.xml file

###2. Import library from gradle

    compile 'com.simsun.scra:library:0.0.2'

###3. Register the observer in your code

Put the below codes to your onCreate callback

    smsObserver = new SmsContentObserver(
        new Handler(),
        YOURACTIVITY.this,
        new String[]{"[your_tag_name]", [your_other_tag_name]},
        smsCode -> {
            if (StringUtil.isPresent(smsCode)) {
                smscodeEt.setText(smsCode);
            }
        }
    );

###4. Unregister the observer in your code

Put the below codes to your onDestory callback

    if (smsObserver != null) {
        smsObserver.unregisterSMSObserver();
        smsObserver = null;
    }
