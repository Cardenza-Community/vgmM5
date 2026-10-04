# Runtime Cardenza support

Based on preserved upstream `3d99db84592f4dca77ab8ea93aa0a2e834d734bc`. Default `unified` and CI-compatible alias `cardenza` use the exact M5Unified fork `203Null/M5Unified@74fe31c6d9a2bd7c04f81eb4f8f0af99262e3bc2` (upstream0.2.24), M5GFX0.2.31, M5Cardputer1.1.1. Hardware is selected at runtime using ES8156 identity; original Cardputer keyboard identity is preserved. The fork owns LED hold, no Cardenza battery ADC/RGB and codec initialization. No app-local hardware HAL or Power/RGB linker wrappers remain.

Same upstream base retained; native runtime Speaker configuration; real local-only catalog exception and dedicated vgm_swap requirement preserved.

The independent `LAUNCHER_NVS_GUARD` and erase wrapper preserve shared Launcher NVS full-partition recovery; normal page GC and app/filesystem erase continue. The actual existing host guard test passes. Existing workflow and prepare.py bytes were preserved; prepare.py generated the raw app image and original dependency licensing notices successfully.

Final publishing-tree build PASS (`pio run -e cardenza`), 924944 bytes, SHA-256 `ebe8550dd2148f24c58e6703040a3dbd9d40151fc9a7e750d6ac4dd7712f76f8`. This image was not flashed or physically validated. Historical device results for earlier images do not prove this image's hardware behavior.

Online catalog is unavailable because six official embedded BIN assets are missing. VGZ decompression and PDX sample mapping require a dedicated named `vgm_swap` partition; this app-only image does not replace the partition table.
