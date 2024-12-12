![GitHub last commit](https://img.shields.io/github/last-commit/spike0en/Pong_Archive)![GitHub repo size](https://img.shields.io/github/repo-size/spike0en/Pong_Archive)[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fspike0en%2FPong-Archive&count_bg=%23754400&title_bg=%235F5F5F&icon=awesomelists.svg&icon_color=%23E7E7E7&title=visitors&edge_flat=false)](https://github.com/spike0en/Pong_Archive)
# Nothing Phone (2) Archive

* A comprehensive collection of unmodified stock OTA images for Nothing Phone (2).

---

## Downloads

- Downloads are tagged with `POST_OTA_VERSION` and `NothingOS version` [here](https://github.com/spike0en/Pong_Archive/releases).

---

## Categories

The stock OTA image files are categorized and archived in `.7z` format based on **boot**, **logical**, and **firmware** categories as follows:

### Boot (marked `-image-boot.7z`)
Includes 7 images:
```bash
boot, dtbo, vendor_boot, recovery, vbmeta, vbmeta_system & vbmeta_vendor
```
### Logical (marked `-image-logical.7z.001-003`)

Includes 6 images:
```bash
system, system_ext, product, vendor, vendor_dlkm & odm
```
### Firmware (marked `-image-firmware.7z`)

Includes 23 images:
```bash
abl, aop, aop_config, bluetooth, cpucp, devcfg, dsp, featenabler, hyp, imagefv, keymaster, modem, multiimgoem, multiimgqti, qupfw, qweslicstore, shrm, tz, uefi, uefisecapp, xbl, xbl_config & xbl_ramdump
```

---

## Disclaimer

- While this is a collection of unmodified images, you still need to have the bootloader unlocked.
- You can re-lock the bootloader after flashing images.
- SHA-1 hash of `<name>-FullOTA.zip` file has been provided. It is to be noted that the built-in NothingOS Offline Updater Tool autonomously verifies file integrity. It initiates the update process only if the file aligns with the hash values specified in `payload-properties.txt`, which is obtained during the creation of the update package.
- Full OTA update packages may not be consistently available for every release. Uploading of the same has currently been discontinued. Users should refer to the release notes and look for links ending with `(full)`, if mentioned, corresponding to the specific build.
- For further inquiries, discussions, and engaging content, users are encouraged to explore the [Nothing Phone (2) Telegram Community](https://t.me/NothingPhone2).

---

## Flashing the Stock ROM Using Fastboot

- Download and use the latest version of Fastboot [directly from Google](https://developer.android.com/tools/releases/platform-tools). Compatible USB drivers can be obtained from [here](https://developer.android.com/studio/run/win-usb). Ensure the `Android Bootloader Interface` is visible in the Device Manager when your device is in bootloader mode before initiating the flashing process.
  
- To flash the stock, unmodified images via Fastboot:
  - Extract the downloaded files using [7zip](https://www.7-zip.org/). If you are using Windows, select the `boot`, `firmware`, and `logical 001-003.7z` files all at once, right-click, and choose **Extract to** `"*\"`. Linux users can use the command `7za -y x "*7z*"`
  - Move all images into a single folder along with the [Pong_fastboot_flasher](https://github.com/HELLBOY017/Pong_fastboot_flasher) script.
  - Run the script, while being connected to the internet, and follow the prompts:
     - Choose whether to wipe data: `(Y/N)`
     - Flash to both slots: `(Y/N)`
     - Disable Android Verified Boot: `(N)`

- Verify that all partitions have been successfully flashed. 
  - If so, choose Reboot to system: `(Y)`
  - If any errors occur, reboot to bootloader and flash again after addressing the cause of failure. Proceeding with `Reboot to system` in such cases may result in a soft or hard bricked device.
    
- If you have any further doubts, refer to this [detailed guide](https://telegra.ph/Guide-for-flashing-Stock-ROM-on-Nothing-Phone-2-04-22).

---

## Updating Procedures:

### A. Manual Sideloading of Incremental OTA Updates:

This can be done using Nothing's built-in Offline Updater Tool, with a **locked bootloader**, as follows:

- Identify the incremental OTA zip files in the release body corresponding to their build numbers. Download the appropriate zip file by clicking on the respective build number. The last one listed is typically the latest.
- Ensure that the incremental OTA package matches the target pre-OTA build version of your device. If the versions do not match, the update will fail. You can verify this by extracting the zip file and checking the `payload_properties.txt`.
- Using a file manager, create a folder named `ota` in the root of your storage.
- Copy the zip file into the newly created `ota` folder.
- Open the dial pad and enter `*#*#682#*#*`.
- The manual update utility will launch, scanning for and locating your downloaded update file.
- Tap to begin the update. The process typically takes 10–15 minutes but may vary.
- Once the update is complete, reboot your device and enjoy the updated software!

### B. Clean Flashing the Full OTA Update Package via Custom Recovery:

- Make sure that your bootloader is unlocked and [OrangeFox Recovery](https://xdaforums.com/t/recovery-12-1-official-orangefox-recovery-project-ofrp.4631141) is installed.
- Flash the `<name>-FullOTA.zip` file (if available in the release) directly using the recovery.
- Format data from the recovery itself after flashing is completed and reboot to system.
- Note that incremental OTA zips **cannot** be flashed using this method.

---

## NothingMuchROM

- You can use this repository to flash non-super partitions to the latest stock to be used with [NothingMuchROM by arter97](https://xdaforums.com/t/nothingmuchrom-for-nothing-phone-2.4623411).
- Make sure to have your dm-verity disabled using the command:
```bash
  fastboot update --disable-verity --disable-verification vbmeta.img
```
- Skip downloading `-logical` files, and follow the above steps during [Pong_fastboot_flasher](https://github.com/HELLBOY017/Pong_fastboot_flasher)'s installation.

---

## Integrity Check

- You can check the downloaded file's integrity with one of the following commands :

``` bash
  md5sum -c *-hash.md5
  sha1sum -c *-hash.sha1
  sha256sum -c *-hash.sha256
  xxh128sum -c *-hash.xxh128
```
- xxh128 is usually the fastest.

---

### Thanks to
- [luk1337](https://github.com/luk1337/oplus_archive) & [arter97](https://github.com/arter97/nothing_archive) for their great work!
- [Hellboy017](https://github.com/HELLBOY017) for his assistance to make the [Pong Fastboot Flasher](https://github.com/HELLBOY017/Pong_fastboot_flasher).

---
