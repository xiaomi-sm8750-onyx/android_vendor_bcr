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

* Minor code style fixes ([PR #882 @chenxiaolong])
* Clarify title and description of telecom-integrated calls option ([Issue #881], [PR #883 @chenxiaolong])
* Minor fixes for new Compose UI ([PR #888 @chenxiaolong])
* Update German translations ([Issue #791], [PR #889 @ElsAr4e])
* Update French translations ([PR #887 @NSO73])

### Version 3.1

* Fix contact name and contact group name not showing up when viewing existing record rule ([PR #880 @chenxiaolong])

### Version 3.0

* Port UI to Jetpack Compose and adopt Material 3 Expressive styling ([PR #878 @chenxiaolong])
* Update Traditional Chinese (zh-TW) translations ([PR #869 @anenasa])
* Update German translations ([Issue #791], [Issue #871], [PR #870 @ElsAr4e], [PR #873 @ElsAr4e])
* Clarify description strings for the record rule initial state setting ([Issue #871], [PR #872 @chenxiaolong])
* Update Simplified Chinese (zh-CN) translations ([PR #874 @lofx-lee])
* Update dependencies ([PR #879 @chenxiaolong])

### Version 2.11

* Update French translations ([PR #857 @NSO73])
* Replace bottom sheet UI layouts with regular preferences ([Issue #858], [PR #862 @chenxiaolong])
* Add mono and stereo suffixes to audio source labels ([Issue #833], [PR #863 @ElsAr4e], [PR #865 @chenxiaolong])
* Make the `, ` separator in the output directory and output format settings summaries translatable ([PR #864 @chenxiaolong])
* Fix titles of switch preferences being truncated when they don't fit ([Issue #858], [PR #866 @chenxiaolong])
* Update German translations ([Issue #791], [PR #867 @ElsAr4e])

### Version 2.10

* Update German translations ([Issue #791], [PR #852 @ElsAr4e])
* Add record rule option to start recordings in the paused state ([Issue #853], [PR #854 @chenxiaolong])

### Version 2.9

* Update German translations ([Issue #791], [PR #837 @ElsAr4e])
* Add Korean translations ([PR #839 @RobertGarciaa])
* Update Chinese translations ([PR #849 @lofx-lee])
* Update dependencies ([PR #851 @chenxiaolong])

### Version 2.8

* Add support for recording uplink or downlink only ([Issue #833], [PR #834 @chenxiaolong])
* Update dependencies ([PR #835 @chenxiaolong], [PR #836 @chenxiaolong])

### Version 2.7

* Update Chinese translations ([PR #827 @lofx-lee])
* Improve workaround for Android binder bug to work in more situations ([Issue #819], [PR #828 @chenxiaolong])

### Version 2.6

* Work around an Android binder bug that sometimes breaks moving recordings to the output directory ([Issue #638], [Issue #732], [Issue #819], [PR #823 @chenxiaolong])
* Fix harmless `Number cannot be empty` log spam for calls from private numbers ([Issue #819], [PR #824 @chenxiaolong])

### Version 2.5

* Add new "package_name" field to call metadata JSON files to indicate which app handled the call ([PR #811 @chenxiaolong])
  * This can be used to differentiate between cellular calls (`com.android.phone`) or telecom-integrated VOIP calls.
* Request InCallService events for self-managed calls ([Issue #804], [PR #812 @chenxiaolong])
  * Improves compatibility for detecting telecom-integrated VOIP calls.
* Add new toggle to make tapping on the completion notification open the output directory instead of the file ([Issue #794], [PR #814 @chenxiaolong])
* Update German translations ([Issue #791], [PR #815 @ElsAr4e])

### Version 2.4

* Fix regression from version 2.2 where recordings were saved to the incorrect directory when subdirectories were used ([Issue #806], [PR #807 @chenxiaolong])
* Disable file retention feature when the filename template has `{date}` more than once ([PR #808 @chenxiaolong])
  * This was not meant to work and could cause the file retention feature to delete unexpected recordings.
  * If you use multiple `{date}` items in the filename template due to subfolders, consider using a single one like `{date:yyyy/yyyy-MM-dd}` instead.
* Fix `{date}` having the wrong value if there was already a custom `{date:...}` before it ([PR #809 @chenxiaolong])

### Version 2.3

* Fix obfuscated log tags after proguard changes in version 2.2 ([PR #801 @chenxiaolong])
* Remove unused `debugOpt` build type ([PR #803 @chenxiaolong])

### Version 2.2

* Update Chinese translations ([PR #793 @lofx-lee])
* Notify when a file could not be moved to the output directory ([Issue #797], [PR #798 @chenxiaolong])
* Reenable default proguard optimizations ([PR #799 @chenxiaolong])
  * For folks who want to decode stack traces from log files, the mapping files are now included with the official releases in `mappings.tar.zst`
* Update dependencies ([PR #800 @chenxiaolong])

### Version 2.1

* Update Chinese translations ([PR #789 @lofx-lee])
* Update German translations ([Issue #791], [PR #792 @ElsAr4e])

### Version 2.0

* Add support for stereo recording ([Issue #124], [Issue #127], [Issue #389], [Issue #405], [Issue #409], [Issue #410], [Issue #500], [Issue #566], [Issue #667], [Issue #673], [PR #772 @chenxiaolong])
  * **NOTE**: This only works if the hardware supports it. Currently, only newer Pixel devices are known to support it.
* Remove "Disable battery optimizations" setting ([PR #773 @chenxiaolong])
  * This setting was never useful since Android does not restrict BCR from launching foreground services anyway.
* Switch to libphonenumber for formatting phone numbers in the output filename ([PR #782 @chenxiaolong])
  * `{phone_number:E.164}` is now guaranteed to actually be E.164-formatted
  * `{phone_number:international}` has been added
  * `{phone_number:formatted}` has been renamed to `{phone_number:national}` and will be automatically migrated
  * `{phone_number:national}` will no longer implicitly fall back to `{phone_number}`
  * `{phone_number:digits_only}` has been removed and will be automatically migrated to `{phone_number}`
* Work around crash on some devices when querying the SIM slot ([Issue #761], [PR #783 @chenxiaolong])
  * This just avoids an Android bug. On affected multi-SIM devices, the SIM slot will still be missing in the recording's filename.
* Remove settings migration for legacy record rules ([PR #777 @chenxiaolong])
  * If upgrading from an old version before 1.75, upgrade to 1.88 first.
* Remove settings migration for legacy notification channels ([PR #778 @chenxiaolong])
  * If upgrading from an old version before 1.24, upgrade to 1.88 first.
* Remove settings migration for direct boot support ([PR #779 @chenxiaolong])
  * If upgrading from an old version before 1.68, upgrade to 1.88 first.
* Update dependencies ([PR #774 @chenxiaolong])
* Fix minor lint warnings ([PR #775 @chenxiaolong], [PR #780 @chenxiaolong])

### Version 1.88

* Fix Russian translation for `notification_recording_finalizing` string ([Issue #763], [PR #764 @Ololoshevich])
* Update AGP to 9.0.0 ([PR #768 @chenxiaolong])

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
