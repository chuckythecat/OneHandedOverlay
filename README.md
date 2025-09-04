# OneHandedOverlay
Create custom developer options display cutout to comfortably use your Android device with one hand.

Based on [NoneDisplayCutout](https://github.com/MlgmXyysd/NoneDisplayCutout/)

On Pixel / AOSP based custom ROM devices, you can just use statusbar height setting in [Iconify](https://github.com/Mahmud0808/Iconify) instead (for me it also worked on Samsung's One UI, but not on Xiaomi's HyperOS)

# Usage

1. Replace every instance of "[dp]" inside of files:

`\DisplayCutoutEmulationNoneOverlay\res\values\strings.xml`

`\noneDisplayCutout\module.prop`

with your desired dp value.

I've used the value of 150 dp on a 1080x2400 6.43" display, which in result gave me a 1080x1987 screen area and 1080x413 notch area.

2. Build using [apktool](https://apktool.org/docs/install/)
```
apktool b DisplayCutoutEmulationNoneOverlay -o cutout.apk
```

3. Sign using [uber apk signer](https://github.com/patrickfav/uber-apk-signer/)
```
java -jar uber-apk-signer.jar --apks cutout.apk
```

4. Move resulting `cutout-aligned-debugSigned.apk` file to `\noneDisplayCutout\system\vendor\overlay\DisplayCutoutEmulationNone\DisplayCutoutEmulationNoneOverlay.apk`

5. Archive the contents of the `noneDisplayCutout` directory to a zip archive.

6. Install resulting zip file using magisk.

7. Go to: Settings -> Developer Options -> "Drawing" section -> Display cutout -> select your dp value

8. Your screen should now be shorter.

# Quirks

In landscape mode your interface is going to look odd or the app is just straight up not going to use your entire notch area.

When you pull up your keyboard, the rest of the viewable area is going to be <sup><sub>really small</sup></sub>