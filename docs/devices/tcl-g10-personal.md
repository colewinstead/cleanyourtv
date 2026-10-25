# Personal TCL G10 setup

This fork preserves a launcher configuration tested on a TCL G10 (`G10_4K_US_NF`),
Android 12, firmware `STT2.230203.001` / AS50. It is based on
[Gathin23/cleanyourtv](https://github.com/Gathin23/cleanyourtv), commit
`34e1c42925268286c9e1c3edca4134cbf9b9cf70`. The upstream MIT license and authorship
are retained. This branch stays on the tested source version; newer upstream
commits have not been installed or verified on this TV.

## Saved configuration

- Dock, left to right: YouTube, YouTube TV, Netflix, Prime Video.
- Live TV / tuner package: `com.tcl.tv`, accessible through Inputs and hidden from the app grid.
- Launcher resource configuration: [config.xml](../../launcher/app/src/main/res/values/config.xml).
- Physical remote mappings: [config.json](tcl-g10-personal/config.json).

The remote JSON maps Netflix, YouTube, Prime Video, Apple TV and Settings. Apply
it using `tools/theme.sh docs/devices/tcl-g10-personal` after building and installing with
`HOME_KEY_SERVICE=1`, following the repository's Home and Wi-Fi safety checks.
Set `TV_HOST` to the TV's current address before using the existing TV tools.

This firmware required the launcher's `APP_AUTO_START` app operation to be
allowed and persisted with `cmd appops write-settings`; the generic `AUTO_START`
operation did not provide the required startup behavior. The private session
notes retain the exact applied commands and restore procedure.

## Verification and limits

On the tested source version, 182 launcher unit tests passed, lint reported no
errors, and the locally built APK was 482,055 bytes. Home, Inputs, dock navigation
and helper startup were checked after reboot. The owner verified all five mapped
physical buttons. Held-volume repeat stopped working with the helper; one press
still changes volume, and the owner accepted this limitation.

The Samba Android package re-enabled after a reboot. Subsequently, Samba
Interactive TV was turned off through Settings > Privacy, which also unchecked
Ad Personalization, Analytics & Measurement, and Third-Party Licensing. All four
remained off after reopening that page; persistence across reboot and actual
network traffic were not tested for this consent change.

Casting, voice, phone remote and firmware updates were retained. End-to-end
casting and voice were not tested. ADB debugging remains enabled at the owner's
request; treat access to the TV and its authorized ADB keys as privileged.

This is a personal configuration record, not a several-day validated debloat
list. Device backups, screenshots, identifiers, credentials, per-device disable
records and recovery files remain local in the ignored directories. The
pre-existing local `PROMPT.md` change is not part of this branch's commit.
