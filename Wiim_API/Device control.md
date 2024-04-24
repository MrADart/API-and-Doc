## Device control

Retrieves detailed informations about a connected device.

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=getStatusEx`

`command`: getStatusEx

**Response:**

```json
{
    "language": "en_us",
    "ssid": "WiiM Pro Plus-A14E",
    "hideSSID": "0",
    "firmware": "Linkplay.4.8.614042",
    "build": "release",
    "project": "WiiM_Pro_Plus",
    "priv_prj": "WiiM_Pro_Plus",
    "project_build_name": "WiiM_Pro_Plus",
    "Release": "20240416",
    "FW_Release_version": "",
    "PCB_version": "3",
    "cast_enable": 0,
    "cast_usage_report": 1,
    "group": "0",
    "wmrm_version": "4.2",
    "expired": "0",
    "internet": "1",
    "uuid": "FF98FCDE8561B66B81EBA065",
    "MAC": "C0:F5:35:30:A1:4E",
    "BTMAC": "c0:f5:35:30:a1:4f",
    "InitialConfiguration": "1",
    "AP_MAC": "C2:F5:35:30:A1:4E",
    "date": "2024:04:24",
    "time": "10:00:25",
    "netstat": "0",
    "essid": "",
    "apcli0": "0.0.0.0",
    "eth0": "172.17.130.69",
    "eth2": "0.0.0.0",
    "ETH_MAC": "00:22:6C:2C:9B:2B",
    "hardware": "AmlogicA113",
    "VersionUpdate": "0",
    "NewVer": "0",
    "mcu_ver": "0",
    "mcu_ver_new": "0",
    "update_check_count": "11",
    "BleRemote_update_checked_counter": "0",
    "ra0": "10.10.10.254",
    "temp_uuid": "2610FD16F2DE7946",
    "cap1": "0x40000400",
    "capability": "0x20084808",
    "languages": "0x1ec",
    "prompt_status": "1",
    "alexa_ver": "20180604",
    "alexa_beta_enable": "0",
    "alexa_force_beta_cfg": "0",
    "dsp_ver": "",
    "ModuleColorNumber": "0",
    "ModuleColorString": "",
    "dsp_ver_new": "",
    "uboot_verinfo": "",
    "kernel_verinfo": "#1 SMP PREEMPT Mon Oct 16 11:28:17 CST 2023",
    "silence_ota_flag": "1",
    "ota_interface_ver": "2.0",
    "streams_all": "0xeff33fd",
    "streams": "0xeff33fd",
    "region": "unknown",
    "volume_control": "0",
    "external": "0x0",
    "preset_key": "12",
    "plm_support": "0x700016",
    "mqtt_support": "1",
    "lbc_support": "0",
    "WifiChannel": "0",
    "RSSI": "0",
    "BSSID": "",
    "wlanSnr": "0",
    "wlanNoise": "0",
    "wlanFreq": "0",
    "wlanDataRate": "0",
    "battery": "0",
    "battery_percent": "0",
    "securemode": "1",
    "upnp_version": "1005",
    "upnp_uuid": "uuid:FF98FCDE-8561-B66B-81EB-A065FF98FCDE",
    "uart_pass_port": "0",
    "communication_port": "8819",
    "web_firmware_update_hide": "0",
    "new_tunein_preset_and_alarm": "1",
    "new_iheart_podcast": "1",
    "tidal_version": "2.0",
    "service_version": "1.0",
    "HiFiSRC_version": "1.0",
    "EQ_support": "Eq4p_ver_2.0",
    "EQVersion": "3.0",
    "audio_channel_config": "1.0",
    "app_timezone_id": "Asia/Yekaterinburg",
    "avs_timezone_id": "Asia/Yekaterinburg",
    "tz_info_ver": "1.0",
    "tz": "5.0",
    "max_volume": "100",
    "power_mode": "-1",
    "security": "https/2.0",
    "security_version": "3.0",
    "security_capabilities": {
        "ver": "1.0",
        "aes_ver": "1.0"
    },
    "public_https_version": "1.0",
    "BleRemoteControl": "1",
    "BleRemoteConnected": "0",
    "autoSenseVersion": "1.0",
    "set_play_mode_enable": "0",
    "privacy_mode": "0",
    "DeviceName": "WiiM Pro Plus-A14E",
    "GroupName": "WiiM Pro Plus-A14E"
}
```

**Value-Description**

| Key                                                        | Value Description                                                                                                 |
| ---------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| uuid                                                       | Device permanent UUID (will remain after device reboot)                                                           |
| DeviceName                                                 | The device UPnP and Airplay friendly name                                                                         |
| GroupName                                                  | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| ssid                                                       | Device's own SSID when in WiFi pairing mode or when device's WiFi hotspot is active                               |
| language                                                   | The language                                                                                                      |
| firmware                                                   | Current firmware version                                                                                          |
| hardware                                                   | Hardware model                                                                                                    |
| build                                                      | Possible values: release, debug, backup                                                                           |
| release: this is a release version                         | debug: this is a debug version                                                                                    |
| backup: this is a backup version                           | project                                                                                                           |
| priv_prj                                                   | Project name which would stand for a specific board                                                               |
| project_build_name                                         | Code identifier for customized release                                                                            |
| Release                                                    | Firmware build date                                                                                               |
| Format: YYYYMMDD                                           | temp_uuid                                                                                                         |
| hideSSID                                                   | When the device is operating as a WiFi hotspot, this flag determines whether its SSID should be hidden or visible |
| 0: ssid is visible                                         | 1: ssid is hidden                                                                                                 |
| SSIDStrategy                                               | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| branch                                                     | Code branch                                                                                                       |
| group                                                      | Wether the device is working slave mode, 0 means master or standalone.                                            |
| master_uuid                                                | Exist when working in slave mode, showing the UUID of master device.                                              |
| slave_mask                                                 | Exist when working in slave mode, showing if the device support mask feature. 0 means not supported.              |
| wmrm_version                                               | Multiroom library version, the latest version 4.2 is not compatible with 2.0.                                     |
| internet                                                   | Current status of internet access:                                                                                |
| 0: not ready                                               | 1: ready                                                                                                          |
| MAC                                                        | MAC address of the device when working in hotspot mode, will show on APP and also the sticker on module/device.   |
| STA_MAC                                                    | MAC address of the STA = STATION                                                                                  |
| CountryCode                                                | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| CountryRegion                                              | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| netstat                                                    | WiFi connect state:                                                                                               |
| 0: no connection                                           | 1: connecting                                                                                                     |
| 2: connected                                               | essid                                                                                                             |
| [hexed string]                                             | apcli0                                                                                                            |
| eth2                                                       | Device's IP address when it's connected to ethernet                                                               |
| ra0                                                        | WiFi AP IP address, normally it is 10.10.10.254                                                                   |
| eth_dhcp                                                   | Flag for DHCP or Static IP Address                                                                                |
| 0: Static IP                                               | 1: IP Address provided by LAN/WLAN DHCP Server                                                                    |
| eth_static_ip                                              | Device's Static IP address (If eth_dhcp=0)                                                                        |
| eth_static_mask                                            | Device's Network Mask (If eth_dhcp=0)                                                                             |
| eth_static_gateway                                         | Device's IP Gateway (If eth_dhcp=0)                                                                               |
| eth_static_dns1                                            | Device's Primary DNS Server (If eth_dhcp=0)                                                                       |
| eth_static_dns2                                            | Device's Secondary DNS Server (If eth_dhcp=0)                                                                     |
| VersionUpdate                                              | Flag that determines, if there is a new firmware version available or not.                                        |
| 0: no new firmware                                         | 1: new firmware available                                                                                         |
| NewVer                                                     | If there is a new firmware available (in case of VersionUpdate is set to 1), this is the new version number       |
| mcu_ver                                                    | Version of MCU on base board                                                                                      |
| mcu_ver_new                                                | New version of MCU on base board, indicates if there is a newer version of MCU available                          |
| 0 - No new version                                         | others - New version                                                                                              |
| dsp_ver                                                    | Version for voice processing, not used                                                                            |
| dsp_ver_new                                                | New version for voice processing, not used                                                                        |
| date                                                       | Current Date                                                                                                      |
| time                                                       | Current local time                                                                                                |
| tz                                                         | Offset of timezone                                                                                                |
| dst_enable                                                 | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| region                                                     | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| prompt_status                                              | Indicates if the prompting voice would be played or not, you can set with command PromptEnable and PromptDisable. |
| 0 - No prompting voice                                     | 1 - Have prompting voice                                                                                          |
| iot_ver                                                    | IOT library version, not used                                                                                     |
| upnp_version                                               | UPnP Device Architecture Version                                                                                  |
| cap1                                                       | Bit mask for the module feature, used internally                                                                  |
| capability                                                 | Bit mask for the module feature, used internally                                                                  |
| languages                                                  | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| streams_all                                                | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| streams                                                    | This is a bit mask:                                                                                               |
| 0: If Airplay is enabled                                   | 1: If DLNA is enabled                                                                                             |
| 2: Has TTPod support                                       | 3: Has TuneIn support                                                                                             |
| 4: Has Pandora support                                     | 5: Has DoubanFM support                                                                                           |
| !! DOCUMENTATION IN PROGRESS !!*                           | external                                                                                                          |
| !! DOCUMENTATION IN PROGRESS !!                            | plm_support                                                                                                       |
| bit1: LineIn (Aux support)                                 | bit2: Bluetooth support                                                                                           |
| bit3: USB support                                          | bit4: Optical support                                                                                             |
| bit6: Coaxial support                                      | bit8: LineIn 2 support                                                                                            |
| bit15: USBDAC support                                      | Others are reserved or not used.                                                                                  |
| preset_key                                                 | Quantity of presets available:                                                                                    |
| spotify_active                                             | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| But I guess:                                               | Flag that indicates if Spotify is currently playing on the device (via Spotify Connect?)                          |
| 0: Spotify is not playing                                  | 1: Spotify is playing                                                                                             |
| lbc_support                                                | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| privacy_mode                                               | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| WifiChannel                                                | The current connected WiFi channel                                                                                |
| RSSI                                                       | RSSI Level of used WiFi                                                                                           |
| Value ranges from 0 - 100. 100 means best signal strength. | BSSID                                                                                                             |
| battery                                                    | 0: battery is not charging                                                                                        |
| 1: battery is charging                                     | battery_percent                                                                                                   |
| Value ranges from 0 - 100                                  | securemode                                                                                                        |
| auth                                                       | Type of WiFi Protected Access used (Authentication Key).                                                          |
| encry                                                      | Type of WiFi Protected Access used (Encryption Protocol).                                                         |
| upnp_uuid                                                  | The UPnP UUID                                                                                                     |
| uart_pass_port                                             | Port used for TCP/IP Communcations/Socket Connections                                                             |
| communication_port                                         | TCP port for internal messages                                                                                    |
| web_firmware_update_hide                                   | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| ignore_talkstart                                           | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| silenceOTATime                                             | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| ignore_silenceOTATime                                      | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| new_tunein_preset_and_alarm                                | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| iheartradio_new                                            | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| new_iheart_podcast                                         | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| tidal_version                                              | TIDAL API version                                                                                                 |
| service_version                                            | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| security                                                   | !! DOCUMENTATION IN PROGRESS !!                                                                                   |
| security_version                                           | !! DOCUMENTATION IN PROGRESS !!                                                                                   |

### Device connection status
This command will return the status of the WiFi connection. The possible return values are as follows.

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=wlanGetConnectState`

`command`: wlanGetConnectState

**Response:**

```string
FAIL
```

**Value-Description**

| Key        | Value Description |
|------------|-------------------|
| `PROCESS`  | Connection still in progress. |
| `PAIRFAIL` | WiFi connection attempt failed. Wrong password given. |
| `FAIL`     | WiFi connection attempt failed. Also this will be the reply for a device that is connected by LAN Ethernet port. |
| `OK`       | Device is connected. |


### Get list of scanned AP's

Retrieves a list of nearby scanned WiFi Access Points and reports some of the main properties. The JSON table results will be sorted by signal strength RSSI

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=wlanGetApListEx`

`command`: wlanGetApListEx

**Response:**

```json
{
   "res": "2",
   "aplist": [
      {
         "auth": "AES",
         "bssid": "b4:fb:e4:f4:73:81",
         "channel": "11",
         "extch": "0",
         "rssi": "37",
         "ssid": "57696E6B656C6761737365"
      },
      {
         "auth": "WPA2PSK",
         "bssid": "18:e8:29:9d:75:c5",
         "channel": "6",
         "encry": "AES",
         "extch": "0",
         "rssi": "24",
         "ssid": "42657465696765757A65556E696669"
      }
   ]
}
```

**Description of Response Values**

| Key     | Value Description |
|---------|-------------------|
| `res`   | Number of SSID's found |
| `aplist`| The key to get the list of scanned Access Points |


**Description of an AP Response Object**

| Key     | Value Description |
|---------|-------------------|
| `auth`  | Required WiFi authorization mechanism |
| `bssid` | The MAC address of that WiFi |
| `channel`| Used WiFi channel |
| `extch` | !! DOCUMENTATION IN PROGRESS !! |
| `rssi`  | RSSI (Received Signal Strength Indication) value<br>Value range is from 0 - 100.<br>100 means best signal strength. |
| `ssid`  | The SSID of that WiFi network<br>[hexed string] |