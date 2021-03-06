# What is push-notifications?
push-notifications is an example of using remote push notification in both Android and iOS. For iOS, Apple Push Notification (APN) and for Android Google Cloud Messaging (GCM) are being used.


# How to execute (iOS)?
1. Dump push_notification.sql on your database.
2. Update database connection string in webservice/index.php line 12
3. Open push-ios project using XCode.
4. Update serviceURL (path to the webservice) in appDelegate.m
5. Change PushIOS.pem file following the [How to create PEM for a push notification enabled app](certificates/HowtocreatePEMforapushnotificationenabledapp.docx)
6. Open webservice/classes/send_push_service.php and and update $passphrase
7. Build the push-ios app using XCode
7. Run push-ios in a device
7. Open webservice/index.php which will show a list of devices. Select anyone of iOS type and press submit to send a push notification


# Information about Apple push notification
1. Apple Push Notification service includes a default Quality of Service (QoS) component that performs a store-and-forward function.

2. If APNs attempts to deliver a notification but the device is offline, the notification is stored for a limited period of time, and delivered to the device when it becomes available.

3. Only one recent notification for a particular app is stored. If multiple notifications are sent while the device is offline, each new notification causes the prior notification to be discarded. This behavior of keeping only the newest notification is referred to as coalescing notifications.

4. If the device remains offline for a long time, any notifications that were being stored for it are discarded.

5. In iOS 8 and later, the maximum size allowed for a notification payload is 2 kilobytes; Apple Push Notification service refuses any notification that exceeds this limit. (Prior to iOS 8 and in OS X, the maximum payload size is 256 bytes.)

# Expiration of GCM push notification
- N/A
 
# How to execute (Android)?
1. Dump push_notification.sql on your database.
2. Update database connection string in webservice/index.php line 12
3. Open android-push project using Eclipse.
4. Update addDeviceURL (path to the webservice) in MainActivity.java (Line 133)
5. Create a project in Google's developers console following [How to create a new project in Google Developers Console](certificates/HowtogetSenderIDandAPIKey.docx)
6. Open android-push/src/net/ujjal/android_push/MainActivity.java (Line 36 ) and update SENDER_ID;
7. Open webservice/classes/send_push_service_android.php (Line 5) and update Google API Key
7. Build the android app using eclipse
7. Run android-push in a device
7. Open webservice/index.php which will show a list of devices. Select anyone of android type and press submit to send a push notification

# References
1. [developer.apple.com](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringPushNotifications/ConfiguringPushNotifications.html)

2. [tutsplus](http://code.tutsplus.com/tutorials/setting-up-push-notifications-on-ios--cms-21925)

3. [raywenderlich](http://www.raywenderlich.com/32960/apple-push-notification-services-in-ios-6-tutorial-part-1)
4. [Apple push notification](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ApplePushService.html)
