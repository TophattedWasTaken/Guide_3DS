# Finalizing Setup

## Required Reading

在載入完 NAND 的內容後，boot9strap 會自動加載 `boot.firm` 中的內容。 In this case, we are using Luma3DS by [LumaTeam](https://github.com/LumaTeam/) to patch the console, allowing it to run homebrew software.

On this page, we will make critical system file backups and install some homebrew programs. Most of these steps will be automated using a script that you will run on your console.

::: info

The script will install the following applications:

- **[FBI](https://github.com/lifehackerhansol/FBI)** _(installs CIA formatted applications)_
- **[Homebrew Launcher Loader](https://github.com/PabloMK7/homebrew_launcher_dummy)** _(launches the Homebrew Launcher)_
- **[Anemone3DS](https://github.com/astronautlevel2/Anemone3DS)** _(installs custom themes)_
- **[Checkpoint](https://github.com/FlagBrew/Checkpoint)** _(backs up and restores save files for 3DS and DS games)_
- **[ftpd](https://github.com/mtheall/ftpd)** _(access your 3DS SD card wirelessly)_
- **[Universal-Updater](https://github.com/Universal-Team/Universal-Updater/)** _(a homebrew app store for downloading homebrew from the 3DS over Wi-Fi)_
- **[GodMode9](https://github.com/d0k3/GodMode9)** _(multipurpose tool which can do NAND and cartridge functions)_

If you don't want one of these applications, you can remove them after you have finished this page by navigating to System Settings -> Data Management -> Nintendo 3DS -> Software. (GodMode9 cannot be removed in this way and is generally required for other functions.)

:::

## Compatibility Notes

::: warning

If your **New 3DS** was on version 2.1.0 before following this guide, you should [restore your NAND backup](godmode9-usage#restoring-a-nand-backup) before continuing. This likely doesn't apply to you unless you were following this guide in 2017.

:::

::: info

如果您先前的自製韌體為基於 EmuNAND 的系統，且您希望將您的 EmuNAND/RedNAND 移植至 SysNAND，請在繼續前進行 [移植 EmuNAND](move-emunand) 頁面中的指示。 如果您不知道 EmuNAND 是什麼的話，這部分大概不適用於您。

:::

## What You Need

- [x_finalize_helper.firm](https://github.com/hacks-guide/finalize/releases/latest/download/x_finalize_helper.firm) (direct download)
- [finalize.romfs](https://github.com/hacks-guide/finalize/releases/latest/download/finalize.romfs) (direct download)

## Instructions

### Section I - Prep Work

In this section, you will copy the files necessary to follow the rest of the instructions on this page.

1. Power off your console
2. 將 SD 卡插入至電腦中
3. Copy `finalize.romfs` to the root of your SD card
4. Open the `luma` folder on your SD card and create a folder named `payloads` inside, if it does not already exist
5. Copy `x_finalize_helper.firm` to the `payloads` folder
6. Reinsert your SD card into your console

The screenshot below indicates the minimum SD card layout that is required to follow this page. 您可能在遵循其他頁面指示中會有一些多的資料夾及檔案在您的 SD 卡中。

::: info

![](/images/screenshots/finalizing-root-layout.png)

:::

::: info

![](/images/screenshots/finalizing-luma-payloads.png)

:::

### Section II - Updating the System

In this section, you will update your system to the latest version, which is safe to do with custom firmware.

<!--@include: ./_include/sysupdate.md -->

### Section III - RTC and DSP setup

In this section, you will sync your 3DS internal clock with the actual time and dump the sound firmware (which is necesssary for some homebrew software to use sound properly).

1. 同時按下『L』+『下』+『Select』鍵以啟動 Rosalina 選單
   - If one of these buttons is broken, download [config.ini](/assets/config.ini) and put it in your `luma` folder, replacing the existing one. This will change the Rosalina menu key combination to (X) + (Y)
2. 選擇『Miscellaneous options』
3. 選擇『Dump DSP firmware』
4. 按『B』繼續
5. 選擇『Nullify user time offset』
6. 按『B』繼續
7. 按『B』回到 Rosalina 主選單
8. 按『B』退出 Rosalina 選單

### Section IV - Setup Script

In this section, you will use a series of scripts to automate homebrew installation, SD card cleanup, and system file backup.

1. Power off your console
2. Press and hold (X), and while holding (X), power on your console. This will launch the Finalizing Setup Helper
   - If you boot to the HOME Menu, your `payloads` folder may be incorrectly spelled or in the wrong location
   - If you encounter an error, consult the [troubleshooting](troubleshooting-finalizing-setup) page
3. If the Helper was successful, your console will boot into GodMode9
   - From this point forward, you can access GodMode9 by holding START while powering on your console
4. 當提示重要檔案備份時，按下『A』繼續，並在完畢後按下『A』繼續
5. 當提示修正 RTC 日期及時間時，按『A』繼續並設定日期及時間，再按『A』繼續
6. 按『Home』鍵以叫出主選單
7. 選擇『Scripts...』
8. Select "finalize"
9. Follow the prompts in the script, answering any questions that you are asked
   - If you encounter an error, follow the instructions in the error message or consult the [troubleshooting](troubleshooting-finalizing-setup) page
10. Once the script says "Setup complete!", press (A) to power off the device
    - If you do NOT see the message "Setup complete!", the script was not successful and you will need to redo this section from Step 3
11. 將 SD 卡插入至電腦中
12. Copy the `/gm9/backups/` folder to a safe location on your computer
    - This folder contains critical file backups and should be backed up to multiple locations (i.e. cloud storage) if possible
    - The two SysNAND files are your NAND backup and can be used to revert your console to a working state if it is bricked by a software issue
    - The `essential.exefs` file contains your console's system-unique files and can be used to recover your data in the event of a hardware failure
13. If you still have them, delete the two `SysNAND` files from the `/gm9/backups/` folder from your SD card
    - The `essential.exefs` file is small and may be kept on your SD card for ease of access

___

::: tip

大功告成！ Custom firmware is now fully configured on your console.

:::

::: info

Trying to figure out what to do with your newly modded device? Visit [our wiki](https://wiki.hacks.guide/wiki/3DS:Things_to_do)!

:::

### Information and Notes

::: info

以下是你該注意的快捷鍵：

- Holding (Select) on boot will launch the Luma3DS configuration menu.
- Holding (Start) on boot will launch GodMode9, or if you have multiple payloads in `/luma/payloads/`, the Luma3DS chainloader.
- By default, pressing (Left Shoulder) + (Down D-Pad) + (Select) while in 3DS mode will open the Rosalina menu, where you can check system information, take screenshots, enable cheats, and more. 這可以從 Rosalina 選單更改。
- Holding (Start) + (Select) + (X) on boot will make the notification LED show a color for debug purposes. See the [changelog](https://github.com/SciresM/boot9strap/releases/tag/1.4) for a list.

:::

::: info

有關如何使用 GodMode9 的各種功能，請見[GodMode9 用法](godmode9-usage) 及 [轉存程式及遊戲卡帶](dumping-titles-and-game-cartridges) 頁面。

:::
