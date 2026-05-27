# liblsl UWP ARM64 Patch

This repository tracks `sccn/liblsl` `v1.16.2` with the minimal changes needed
for UWP ARM64 builds:

- Skip the `lslver` tool for `WINDOWS_STORE` builds.
- Avoid Win32 timer-resolution APIs when building for `WINAPI_FAMILY_APP`.

Example CMake configuration:

```powershell
cmake `
  -S . `
  -B build\uwp-arm64 `
  -G "Visual Studio 17 2022" `
  -A ARM64 `
  -DCMAKE_SYSTEM_NAME=WindowsStore `
  "-DCMAKE_SYSTEM_VERSION=10.0" `
  -DCMAKE_TRY_COMPILE_TARGET_TYPE=STATIC_LIBRARY `
  -DLSL_BUILD_EXAMPLES=OFF `
  -DLSL_UNITTESTS=OFF `
  -DLSL_TOOLS=OFF `
  -DLSL_BUNDLED_BOOST=ON `
  -DLSL_BUNDLED_PUGIXML=ON `
  -DLSL_SLIMARCHIVE=ON `
  -DLSL_WINVER=0x0A00
```

