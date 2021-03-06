Version 0.2.0 - October 27, 2014
--------------------------------

Enhancements:

- Add `ProximityKitManager#stop()` to the public API

  This stops any further syncing with the cloud. It additionally, unregisters
  any beacons and geofences which are being monitored.
- Attempts to auto update database of Android model specific distance
  calculations
- Added generation of beacon bytearrays from BeaconParser in support of future
  transmitter on release of Android


Version 0.1.1 - October 23, 2014
--------------------------------

Bug Fixes:

- Fix erroneous warning when geofence action queue has been emptied and a new
  action is added. This fix also causes the new action to start running.
- Fix race condition reporting erroneous warning caused by multi-step actions
  are rapidly added to the queue.
- Fix `ClassCastException` caused if the AltBeacon `BeaconManager` is created
  prior to the Proximity Kit manager being instantiated.
- Uses distance calculations specific to the Android model
- Fix bug with RegionBootstrap setting background mode incorrectly on app
  launch


Version 0.1.0 - September 4, 2014
---------------------------------

- Requires JDK 1.7+
- Requires Android minimum SDK version 9+
- [AltBeacon.org](http://altbeacon.org/) support for monitoring beacon regions
  using the v1.0 specification
- Uses [AltBeacon/android-beacon-library](https://github.com/AltBeacon/android-beacon-library)
  version [2.0-beta6](https://github.com/AltBeacon/android-beacon-library/releases/tag/2.0-beta.6)
- Geofence support using [Google Play
  services](https://developer.android.com/google/play-services) 4.4+

Major technical focuses for this release were on adding geofence and AltBeacon
v1.0 spec support. Receiving notification of various events is provided by
registering as one or more a callbacks. These callbacks are defined by several
interfaces based on the activity and type of region.

- `ProximityKitMonitorNotifier`

  Notifies the app when the host device has come with-in or moved out-of
  proximity with any of the registered beacons.

- `ProximityKitRangeNotifier`

  Available while the host device is with-in a registered beacon regions.
  Provides the app with constant notifications about the device's relative
  proximity to those regions.

- `ProximityKitGeofenceNotifier`

  Notifies the app when the host device has come with-in or moved out-of
  any of the registered geofence regions.

- `ProximityKitSyncNotifier`

  Notifies the app after Proximity Kit has been synced with the cloud.
