
## USB Configuration Tool
To configure some Femtofox settings such as wifi, you can insert a USB flash drive containing a configuration file. The system will automatically recognize, mount and implement the settings you specify.
Configurable settings are:

 - Wifi SSID
 - Wifi PSK (password)
 - Wifi country
 - Timezone
 - Meshtastic:
     - LoRa radio model
	 - [URL](https://meshtastic.org/docs/software/python/cli/#--seturl-seturl) (used to configure LoRa settings and channels)
	 - Security: Add Admin Key
	 - Security: Clear Admin Key List
	 - Security: [Legacy Admin Channel](https://meshtastic.org/docs/configuration/radio/security/#admin-channel-enabled) enable/disable

### Instructions
The USB drive must be formatted with a single FAT32, exFAT, NTFS (read only - log will not be saved to drive) or ext4 partition. Add a file named `femtofox-config.txt` and whichever of the the following lines you want to set, keeping in mind this is CaSe sEnSiTiVe:
```
wifi_ssid="Your SSID name"
wifi_psk="wifipassword"
wifi_country="US"
timezone="America/New_York"
meshtastic_lora_radio="ebyte-e22-900m30s"
meshtastic_url="https://meshtastic.org/e/#CgMSAQESCAgBOAFAA0gB"
meshtastic_admin_key="base64:T/b8EGvi/Nqi6GyGefJt/jOQr+5uWHHZuBavkNcUwWQ="
meshtastic_legacy_admin="true"
```
> [!NOTE]
> Enter as many or as few settings as you like.
> 
> For `wifi_country`, insert your country's two letter code (such as CA or IN) in capital letters.
> 
> Use a timezone as it appears in [the tz database](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
>
> **Meshtastic**
> For `meshtastic_lora_radio`, choose your radio from the supported hardware list.
> Options are: 
> * `femtofox_SX1262_TCXO` *(for pretty much every module with TCXO)*
> * `femtofox_SX1262_XTAL` *(for Ebyte E22-900MM22S, AiThinker RA01SH, and Waveshare Pi hat)*
> * `femtofox_LR1121_TCXO` *(for Ebyte E80-900M2213S)*
> * `none` *(for simradio)*
> 
>
>To add a `meshtastic_admin_key`, copy it from the app and add `base64:` to the beginning (`meshtastic_admin_key="base64:T/b8EGvi/Nqi6GyGefJt/jOQr+5uWHHZuBavkNcUwWQ="`).
>
> Clearing the `meshtastic_admin_key` list: The admin key list can contain up to three keys - *if more are added they will be ignored*. The USB configuration tool supports clearing the admin key list, after which you will need to re-add your admin key/s in a second operation. To clear the admin key list, enter `meshtastic_admin_key="0"`, without `base64:`.

> [!CAUTION]
> Attempting to set wifi settings via USB configuration tool without a wifi adapter connected will lead to a 5 minute hang while the configuration tool runs - either disconnect and reconnect power or wait the full 5 minutes to to recover.

**To apply your configuration, reboot the Femtofox with the USB drive plugged in. No other USB drives can be plugged in at the same time.**
A log (`femtofox-config.log`) is saved to `/home/femto` and the USB drive (except on NTFS, which is read only).
<br>
### Boot codes
When the Femtofox is finished booting, it will blink its User LED (see below) in a pattern which can be used to gather info on its status or help diagnose issues.
![LEDs](https://github.com/noon92/femtofox/blob/main/leds.png)
| LED blink pattern | Meaning | Possible causes | Solutions |
|--|--|--|--|
|<center>⚠️<br>________________<br>1 very long blink, lasting 5 seconds| Failed to mount USB drive. Ignoring.| <li>Invalid filesystem<li>Corrupted partition table<li>Defective USB drive<li>Defective USB OTG adapter | <li>Use a supported partition (FAT32, exFAT, NTFS, ext4)<li>Repair partition table<li>Try another USB drive<li>Try another USB OTG adapter |
|<center>⚠️<br>\_\_\_\_\_&nbsp;&nbsp;\_\_\_\_\_&nbsp;&nbsp;\_\_\_\_\_<br>3 long blinks, each lasting 1.5 seconds | USB drive mounted successfully but femtofox-config.txt was not found. Ignoring.| Config file missing. | Create configuration file as described above. |
|<center>⚠️<br>\_\_\_\_\_&nbsp;&nbsp;\_\_\_\_\_&nbsp;&nbsp;\_\_\_\_\_&nbsp;&nbsp;\_\_\_\_\_&nbsp;&nbsp;\_\_\_\_\_<br>5 long blinks, each lasting 1.5 seconds | USB drive mounted successfully and femtofox-config.txt was found but did not contain readable configuration data. Ignoring.| Configuration file improperly formatted or contains no data. | Check configuration file contents as described above. |
|<center>⚠️<br>\_\_\_&nbsp;&nbsp;\_\_\_&nbsp;&nbsp;\_&nbsp;&nbsp;\_&nbsp;&nbsp;\_\_\_&nbsp;&nbsp;\_\_\_&nbsp;&nbsp;\_&nbsp;&nbsp;\_<br>2 long blinks, each lasting 1 seconds, then 2 short blinks, each lasting 1/4 of a second. Repeats twice | Error while trying to implement a Meshtastic setting after 3 attempts. Some settings may have been implemented successfully.| <li>The error may be transient.<li>Configuration file may contain improper data. | <li>Try again.<li>Check configuration file contents as described above.<li>Check the log.<br><br>This pattern may flash before other patterns. The pattern will repeat once for each failed setting.|
|<center>✅<br>. . . . . . . . . .<br>10 very fast blinks, each lasting 1/8th of a second | USB drive mounted successfully, and femtofox-config.txt was found and contained configuration data which was sent for deployment. Any affected services will now restart. You can disconnect the USB drive. | This does not mean that the information in the config file is correct - only that it was readable.<br>Note that the "success" boot code will flash if at least one setting is successfully read - even if the setting was not implemented successfully.|
|<center>✅<br>\_\_&nbsp;&nbsp;\_\_&nbsp;&nbsp;\_\_&nbsp;&nbsp;\_\_&nbsp;&nbsp;\_\_<br>5 medium blinks, each lasting 0.5 seconds | Boot complete. Appears on every successful boot and always appears last.| | |
 
> [!NOTE]
> Boot codes can appear in sequence - for example: one long (4 second) blink, followed by 5 medium (half second) blinks means the attempt to mount the USB drive failed, and that boot is complete.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMTE4MzAwNjVdfQ==
-->