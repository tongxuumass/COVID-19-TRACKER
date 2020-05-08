Original code from here:
https://github.com/miracleyoo/COVID-19-APP/commits/master

(API key in gradle.properties also needs to be updated)

Here's the documentation of my COVID-19 app.

I basically implemented 3 buttons, "START", "LOCATIONS", and "DEVICES", and also added some settings in the form of a CheckBox ("filter phones") and an EditText ("notification frequency").

To begin using the app, press the "START" button, which will begin a scan. The app will begin to perform two tasks on a recurrent timer. Every ten seconds, it will scan for any popular nearby attractions. It will then check if the user is currently at any of those attractions by checking if the user's location is within a small distance. Those visited attractions and the time of visit will be added to a list, which we can view if we press the "LOCATIONS" button. Any visited locations throughout the scan will be visualized on the map. In addition, every ten seconds it will also scan for any nearby Bluetooth devices. Any nearby devices and the times of encounter will also be added to a list, which we can if view by pressing the "DEVICES" button. For both cases, we don't keep duplicates, so we track the number of unique locations or devices encountered. This update will continuously happen quietly, but we can also set a "notification frequency", which is in seconds. This sets the frequency at which the user gets update about his social distance scores, or the numbers of places and devices they've encountered. We also have a "filter phones" option. If this is checked, only phones will be counted towards the number of devices encountered, since we can assume (as Zhongyang said) that some people can own multiple Bluetooth devices but only one phone. So this gives a better metric of the actual number of people we've come close to. To stop the scan, we just exit the app.

If kept running throughout the day, the app should calculate a decent estimation of the user's social distance score, via the number of public locations visited, and an approximate number of people the user came close to (via proximal Bluetooth device count).

One weakness of this app is that it needs to be focused to work. Exiting to background will cause unusual behavior.

Specifically, the things I've done:
- Rewired the "Get Place" and "Nearby Devices" functionality to be a single button.
- Implemented a recurring timer that scans repeatedly.
- Return the list of devices and locations encountered on top of number.
- Add a way to calculate distance between current location and nearby locations, and use this to gauge whether to add locations.
- Add a way to filter out BlueTooth devices so only phones are kept.
- Update the user of social distance scores based on user-desired frequency.

I also locked screen orientation to prevent losing variables due to phone rotation.

I essentially copied and stitched around the starter code, with other code snippets I've taken from online documentation and StackExchange posts (see the code for detailed citations). I didi copy certain code fragments for various functionalities off the web, which I've cited in the code.

A list of all sources I've referenced are below:

https://wangjingke.com/2016/09/23/Multiple-ways-to-schedule-repeated-tasks-in-android

https://stackoverflow.com/questions/40471/differences-between-hashmap-and-hashtable

https://developer.android.com/reference/java/util/Hashtable

https://developer.android.com/reference/java/util/Dictionary

https://www.geeksforgeeks.org/set-list-java/

https://beginnersbook.com/2014/08/how-to-iterate-over-a-sethashset

https://howtodoinjava.com/java/basics/java-tuples/

https://stackoverflow.com/questions/6010018/bind-method-to-a-button-in-android

https://stackoverflow.com/questions/35578586/background-process-timer-on-android

https://stackoverflow.com/questions/45925530/android-timer-in-service-how-to-stop-and-start

https://developer.android.com/reference/androidx/car/cluster/navigation/LatLng

https://developer.android.com/reference/android/location/Location

https://www.geeksforgeeks.org/set-in-java/

https://www.w3schools.com/java/java_arraylist.asp

https://stackoverflow.com/questions/17711656/how-to-get-all-elements-of-an-arrayadapter

https://developer.android.com/reference/android/widget/ArrayAdapter

https://stackoverflow.com/questions/4030115/how-to-pass-arraylist-using-putstringarraylistextra

https://stackoverflow.com/questions/5265913/how-to-use-putextra-and-getextra-for-string-data

https://stackoverflow.com/questions/3848148/sending-arrays-with-intent-putextra

https://www.w3schools.com/java/java_for_loop.asp

https://developer.android.com/reference/android/widget/ArrayAdapter#getCount()

https://developer.android.com/guide/components/services

https://developer.android.com/reference/android/bluetooth/BluetoothClass.Device

https://stackoverflow.com/questions/5274354/how-can-we-increase-the-font-size-in-toast

https://stackoverflow.com/questions/4675750/lock-screen-orientation-android

https://www.geeksforgeeks.org/arrays-in-java/

https://developer.android.com/reference/android/bluetooth/BluetoothClass

https://developer.android.com/reference/android/bluetooth/BluetoothDevice#getType()

https://stackoverflow.com/questions/18336151/how-to-check-if-android-checkbox-is-checked-within-its-onclick-method-declared

https://developer.android.com/reference/android/widget/CheckBox

https://stackoverflow.com/questions/4542318/android-append-text-file

https://stackoverflow.com/questions/14376807/read-write-string-from-to-a-file-in-android

https://stackoverflow.com/questions/2709253/converting-a-string-to-an-integer-on-android

https://developer.android.com/guide/topics/ui/controls/spinner

https://developer.android.com/training/keyboard-input/style

https://developer.android.com/reference/android/text/InputType

https://developer.android.com/reference/android/widget/EditText

https://developer.android.com/reference/android/bluetooth/BluetoothClass.Device

https://developer.android.com/reference/android/bluetooth/BluetoothClass.Device#PHONE_CELLULAR

https://developer.android.com/reference/android/bluetooth/BluetoothClass.Device#AUDIO_VIDEO_CAMCORDER





 


