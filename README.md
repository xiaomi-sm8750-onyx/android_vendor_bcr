## Add In Rom

Add This Line In device.mk

$(call inherit-product, vendor/bcr/bcr.mk)

# Basic Call Recorder

<img src="app/images/icon.svg" alt="app icon" width="72" />

[![latest release badge](https://img.shields.io/github/v/release/chenxiaolong/BCR?sort=semver)
[![license badge](https://img.shields.io/github/license/chenxiaolong/BCR)

BCR is a simple Android call recording app for rooted devices or devices running custom firmware. Once enabled, it stays out of the way and automatically records incoming and outgoing calls in the background.

<img src="app/images/light.png" alt="light mode screenshot" width="200" /> <img src="app/images/dark.png" alt="dark mode screenshot" width="200" />

## Features

* Supports Android 9 and newer
* Supports output in various formats:
* OGG/Opus - Lossy, smallest files, default on Android 10+
* M4A/AAC - Lossy, smaller files, default on Android 9
* FLAC - Lossless, larger files
* WAV/PCM - Lossless, largest files, least CPU usage
* Supports Android's Storage Access Framework (can record to SD cards, USB devices, etc.)
* Direct boot aware (records calls prior to first unlock after a reboot)
* Per-contact auto-record rules
* Quick settings toggle
* Material You dynamic theming
* No persistent notification unless a recording is in progress
* No network access permission
* Works with call screening on Pixel devices (records the caller, but not the automated system)

### Unreleased

* Fix Russian translation for `notification_recording_finalizing` string ([Issue #763], [PR #764 @Ololoshevich])

### Version 1.87

* Add support for using Unix timestamps in the filename template ([Issue #742], [PR #743 @chenxiaolong])

### Version 1.86

* Update French translations ([PR #734 @NSO73])
* Work around broken root hiding mechanisms that hide the old sysconfig file from the system ([Issue #733], [PR #736 @chenxiaolong])
* Update dependencies ([PR #737 @chenxiaolong])

### Version 1.85

* Add support for hiding the app icon ([Issue #727], [PR #728 @People-11])
  * When hidden, the app can be opened by dialing `*#*#BCR#*#*` (`*#*#227#*#*`)

### Version 1.84

* Fix recording to output directories that do not support seekable files ([Issue #722], [PR #723 @yeicor])
* Append file extension manually if the SAF provider for the output directory fails to do so ([PR #724 @chenxiaolong])
* Show path in notifications when SAF URI is meaningless ([PR #725 @chenxiaolong])

### Version 1.83

* Fix recording being restarted if the call state changes after it was cancelled (eg. due to "ignore" rules) ([Issue #719], [PR #720 @chenxiaolong])

### Version 1.82

* Fix file retention setting not refreshing if it was disabled by a bad filename template and the template is reset via long press ([PR #717 @chenxiaolong])
* Update dependencies ([PR #718 @chenxiaolong])

### Version 1.81

* Add Azerbaijani translations ([PR #713 @muctebanesiri])
* Update dependencies ([PR #714 @chenxiaolong])

### Version 1.80

* Update dependencies ([PR #696 @chenxiaolong], [PR #705 @chenxiaolong])
* Remove dependency info block from APK ([PR #704 @chenxiaolong])

### Version 1.79

* Target Java 21 ([PR #685 @chenxiaolong])
* Replace FAT32-invalid code points and ignorable code points in filenames ([Issue #691], [PR #692 @chenxiaolong], [PR #692 @TheDeathDragon])
* Update dependencies ([PR #693 @chenxiaolong])

### Version 1.78

* Add new `duration_secs_wall` field to the metadata JSON output file ([PR #674 @chenxiaolong])
* This measures the wall time from when the recording process started to when it ended. This value can be compared with `duration_secs_total` to determine if Android is sending too little audio to BCR.
* Add Persian translations ([PR #681 @namini40])
* Update dependencies and target API 36 ([PR #684 @chenxiaolong])

### Version 1.77

* Update Italian translations ([PR #653 @nicorac])
* Update Hebrew translations ([PR #655 @tzagim])
* Update dependencies ([PR #665 @chenxiaolong])

### Version 1.76

* Update French translations ([PR #651 @NSO73])
* Assume that `android.hardware.telephony.subscription` is supported on Android 11+ ([Issue #649], [PR #652 @chenxiaolong])
* OxygenOS on OnePlus devices supports this feature, but does not declare that it does. This workaround allows features that depend on the SIM slot (eg. SIM slot rules) to work.

### Version 1.74

* Update French translations ([PR #627 @NSO73])
* Work around crash in Android itself when querying sample rates on older Android versions ([Issue #628], [PR #629 @chenxiaolong])
* Work around crash when accessing private Android APIs in Android 9 ([Issue #628], [PR #630 @chenxiaolong])
* Update all dependencies ([PR #631 @chenxiaolong])
* Work around Android 9 and 10 not knowing the file extension for the `audio/mp4` MIME type ([PR #632 @chenxiaolong])

### Version 1.73

* Update French translations ([PR #615 @NSO73])
* Add Romanian translations ([PR #613 @gilav23])
* Add debug option to save log file ([PR #622 @chenxiaolong])
* Fix another Cursor resource leak ([PR #623 @chenxiaolong])
* Show error message if contact group picker fails to query the list of groups ([Issue #620], [PR #624 @chenxiaolong])
* Enable predictive back gestures ([PR #625 @chenxiaolong])
* Don't fail to populate contact group list when the SOURCE_ID is null ([Issue #620], [PR #626 @chenxiaolong])
* Add account name to contact group list ([Issue #620], [PR #626 @chenxiaolong])

### Version 1.72

* Add support for specifying a minimum duration for keeping a recording ([Issue #411], [Issue #604], [PR #605 @chenxiaolong])
* Add support for contact groups in auto-record rules ([Issue #536], [PR #606 @chenxiaolong])
* Fix Cursor resource leak ([PR #610 @chenxiaolong])
* Minor notification code cleanup ([PR #611 @chenxiaolong])
* Update dependencies ([PR #612 @chenxiaolong])

### Version 1.71

* Fix notification not showing after recording to the default output directory ([PR #603 @chenxiaolong])

## Non-features

As the name alludes, BCR intends to be a basic as possible. The project will have succeeded at its goal if the only updates it ever needs are for compatibility with new Android versions. Thus, many potentially useful features will never be implemented, such as:

* Support for old Android versions (support is dropped as soon as maintenance becomes cumbersome)
* Workarounds for [OEM-specific battery optimization and app killing behavior](https://dontkillmyapp.com/)
* Workarounds for devices that don't support the [`VOICE_CALL` audio source](https://developer.android.com/reference/android/media/MediaRecorder.AudioSource#VOICE_CALL) (eg. using microphone + speakerphone)
* Support for direct boot mode (the state before the device is initially unlocked after reboot)
* Support for stock, unrooted firmware

## Credits

Thanks to [chenxiaolong](https://github.com/chenxiaolong) For Base Repo And [StudioKeys](https://github.com/StudioKeys) For Helping Me
