# Local-Notification

import 'package:flutter_local_notifications/flutter_local_notifications.dart';

class NotificationService {
  final noticationPluggin = FlutterLocalNotificationsPlugin();

  final _androidSetting = AndroidInitializationSettings('logo');

  void initilizedNotification() async {
    final _initilizedSetting = InitializationSettings(android: _androidSetting);
    await noticationPluggin.initialize(
      _initilizedSetting,
    );
  }

  void sendNotification(String title, String body) async {
    final androidNotificationDetails = AndroidNotificationDetails(
        'challed id', 'challen name',
        importance: Importance.max, priority: Priority.max);

    final notificationDetails =
        NotificationDetails(android: androidNotificationDetails);
    await noticationPluggin.show(0, title, body, notificationDetails);
  }

  void PeriodecNotification(String title, String body) async {
    final androidNotificationDetails = AndroidNotificationDetails(
        'challed id', 'challen name',
        importance: Importance.max, priority: Priority.high);

    final notificationDetails =
        NotificationDetails(android: androidNotificationDetails);
    await noticationPluggin.periodicallyShow(
        0, title, body, RepeatInterval.everyMinute, notificationDetails);
  }

  void stopNotification() {
    noticationPluggin.cancel(0);
  }
}
