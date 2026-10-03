# Cardenza support

Build `pio run -e cardenza -j4` with PlatformIO Espressif32 6.7.0/Arduino 2.0.16. This target is explicitly offline: the upstream six embedded online-catalog BIN files are absent from Git. No fabricated database is supplied; local SD browsing/playback is retained, online catalog is unavailable.

Plain VGM streams from SD without PSRAM; compressed VGZ playback requires the upstream named `vgm_swap` data partition. Its existence/size is a Launcher installation concern, and is not guaranteed by this app-only BIN. The diagnostic harness provides a 3 MB swap partition. MDX support remains enabled. Physical playback is pending device verification.

Hardware: original Cardputer V1 matrix keyboard/display/SD; ES8156 DAC at I2C 0x08 (SDA2/SCL1); stereo Philips I2S, 16-bit slots, BCLK41/LRCK43/DOUT42. The shared MIT header is vendored from `../shared/cardenza_hal.h` with its license. It verifies codec identity/registers before peripheral setup and holds keyboard LED EN21 high. GPIO38 remains LCD backlight. No gyro, battery ADC, charging management or WS2812 output is enabled for this target. Buffers use internal RAM; no PSRAM is assumed.

These are app-only images for installation through the Cardenza Launcher. Do not flash a project-generated partition table/bootloader over the Launcher. Upstream targets retain their original behavior. Compilation and source review are separate from physical UI, audio, microphone and SD validation; verify these on target hardware before a release.

M5Unified 0.2.22 is pinned (separate translation units). Two linker wrappers suppress Power.begin and RGB setup. A newer unity-build M5Unified cannot use this wrapper technique safely. Verify the final ELF has only `__wrap__ZN2m511Power_Class5beginEv` and `__wrap__ZN2m59M5Unified10_setup_ledEN4lgfx6boards7board_tE`, without their original definitions. This matters because GPIO10 is a USB switch control on Cardenza, not a battery ADC. PlatformIO may retain both a transitive latest library and the exact pinned version; the build graph/compiled path and ELF must match the pinned version.

Official catalog recovery check (2026-10-01): [upstream src/db_installer.txt](https://raw.githubusercontent.com/Layer812/vgmM5/main/src/db_installer.txt) instructs users to run `build_db.py` to generate the six BIN files, but a read-only scan of all 58 upstream commits found neither that generator/input metadata nor the six assets. The remote has only `main`, no tags, and [official Releases](https://github.com/Layer812/vgmM5/releases) contains no release assets. The README supplies a complete-firmware M5Burner share code, without a catalog package. An author-provided generator plus input metadata, or six matching real BIN files, is needed to unblock the full online build. No successful stock/full-online build is claimed; the existing offline Cardenza candidate remains current.

Cardenza initializes USB HWCDC once and waits at most one second for host reconnection before startup diagnostics. The Arduino 2.0.16 HWCDC implementation re-enumerates USB on every begin call; flush while disconnected discards queued output. Repeated startup begin calls and unconditional disconnected flushes have therefore been removed only for Cardenza. Previous silent captures remain boot-unconfirmed, not proof of a panic. The fresh logging image needs device verification.

## Licensing

The upstream repository does not supply an application license. This GitHub fork
preserves upstream source and attribution; the MIT license next to the Cardenza
HAL applies only to that HAL. It does not grant permission to redistribute the
upstream application or its dependencies in binary form. No release BIN is
published by this port until those permissions are resolved.

The Cardenza build rejects full DATA/NVS partition erases, including Arduino
startup recovery that would clear the Launcher's shared settings. Normal NVS
writes and erases of other explicitly selected partitions are unaffected. An
NVS recovery error requires deliberate repair rather than automatic deletion.
