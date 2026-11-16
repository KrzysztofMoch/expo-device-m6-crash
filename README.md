# expo-device crash on Apple M6 simulator hosts

A blank Expo app (`npx create-expo-app --template blank`) plus `expo-device`.
`App.js` renders `Device.supportedCpuArchitectures`.

In the iOS simulator on an Apple M6 Mac, the app exits with SIGTRAP about 1s
after launch, right after `Creating JS object for module 'ExpoDevice'`.
`NXGetLocalArchInfo()` returns NULL there and `cpuArchitectures()` in
`expo-device/ios/DeviceModule.swift` dereferences it.

```sh
npm install
npx expo run:ios --configuration Release
```
