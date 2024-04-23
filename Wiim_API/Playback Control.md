## Playback Control

### Playback Status

Getting player status (Yeah, it's that simple)

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=getPlayerStatus`

- `command`: getPlayerStatus 
  
  **Response:
  
  ```json
  {
    "type": "0",
    "ch": "0",
    "mode": "10",
    "loop": "0",
    "eq": "0",
    "vendor": "",
    "status": "stop",
    "curpos": "73587",
    "offset_pts": "73587",
    "totlen": "0",
    "Title": "",
    "Artist": "",
    "Album": "",
    "alarmflag": "0",
    "plicount": "0",
    "plicurr": "0",
    "vol": "48",
    "mute": "0"
  }
  ```

Description of Response Values

| Key          | Value Description                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `type`       | `0`: Main or standalone device `1`: Device is a Multiroom Guest                                                                                                                                                                                                                                                                                                                                                                                                     |
| `ch`         | Active channel(s) `0`: Stereo `1`: Left `2`: Right                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `mode`       | Playback mode `0`: Idling `1`: airplay streaming `2`: DLNA streaming `10`: Playing network content, e.g. vTuner, Home Media Share, Amazon Music, Deezer, etc. `11`: playing UDISK(Local USB disk on Arylic Device) `20`: playback start by HTTPAPI `31`: Spotify Connect streaming `40`: Line-In input mode `41`: Bluetooth input mode `43`: Optical input mode `47`: Line-In #2 input mode `51`: USBDAC input mode `99`: The Device is a Guest in a Multiroom Zone |
| `loop`       | Is a Combination of SHUFFLE and REPEAT modes `0`: SHUFFLE: disabled REPEAT: enabled - loop `1`: SHUFFLE: disabled REPEAT: enabled - loop once `2`: SHUFFLE: enabled REPEAT: enabled - loop `3`: SHUFFLE: enabled REPEAT: disabled `4`: SHUFFLE: disabled REPEAT: disabled `5`: SHUFFLE: enabled REPEAT: enabled - loop once                                                                                                                                         |
| `eq`         | The current Equalizer setting                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `status`     | Device status `stop`: no audio selected `play`: playing audio `load`: load ?? `pause`: audio paused                                                                                                                                                                                                                                                                                                                                                                 |
| `curpos`     | Current playing position (in ms)                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `offset_pts` | !! DOCUMENTATION IN PROGRESS !!                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `totlen`     | Current track length (in ms)                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `Title`      | [hexed string] of the track title                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `Artist`     | [hexed string] of the artist                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `Album`      | [hexed string] of the album                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `alarmflag`  | !! DOCUMENTATION IN PROGRESS !!                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `plicount`   | The total number of tracks in the playlist                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `plicurr`    | Index of current track in playlist                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `vol`        | Current volume Value range is from 0 - 100. So can be considered a linear percentage (0% to 100%)                                                                                                                                                                                                                                                                                                                                                                   |
| `mute`       | The mute status `0`: Not muted `1`: Muted                                                                                                                                                                                                                                                                                                                                                                                                                           |

### Select Input Source

Selects the Audio Source of the Device. The available audio sources for each device will depend on the installed hardware.

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=setPlayerCmd:switchmode:<player_mode>`

`command`: setPlayerCmd:switchmode

**Parameters:**

| Parameter     | Description                              |
| ------------- | ---------------------------------------- |
| `player_mode` | The audio source that has to be switched |
|               | `wifi`: wifi mode                        |
|               | `line-in`: line analogue input           |
|               | `bluetooth`: bluetooth mode              |
|               | `optical`: optical digital input         |
|               | `co-axial`: co-axial digital input       |
|               | `line-in2`: line analogue input #2       |
|               | `udisk`: UDisk mode                      |
|               | `PCUSB`: USBDAC mode                     |

**Response:**

200 OK 

### Set Shuffle And Repeat Mode

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=setPlayerCmd:switchmode:<player_mode>`

`command`: setPlayerCmd:switchmode

**Parameters:**

| Parameter | Description                                         |
| --------- | --------------------------------------------------- |
| `mode`    | Activates a combination of Shuffle and Repeat modes |
|           | `0`: Shuffle disabled, Repeat enabled - loop        |
|           | `1`: Shuffle disabled, Repeat enabled - loop once   |
|           | `2`: Shuffle enabled, Repeat enabled - loop         |
|           | `3`: Shuffle enabled, Repeat disabled               |
|           | `4`: Shuffle disabled, Repeat disabled              |
|           | `5`: Shuffle enabled, Repeat enabled - loop once    |

**Response:**

200 OK

### Control The Playback

Control the current playback

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=setPlayerCmd:switchmode:<player_mode>`

`command`: setPlayerCmd

**Parameters:**

| Parameter  | Description                                                   |
| ---------- | ------------------------------------------------------------- |
| `pause`    | Pause playback                                                |
| `resume`   | Resume playback from last position, if it is paused           |
| `onepause` | Toggle Play/Pause                                             |
| `stop`     | Stop current playback and removes selected source from device |
| `prev`     | Play previous song in playlist                                |
| `next`     | Play next song in playlist                                    |

**Response:**

200 OK

### Seeking

Seek with seconds for current playback, have no use when playing radio link.

P.S. Only works for sources adjusted from the **Wiim Home** app.  

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=setPlayerCmd:seek:<position>`

`command`: setPlayerCmd:seek <position>

**Parameters:**

| Parameter  | Description                    |
| ---------- | ------------------------------ |
| `position` | Position to seek to in seconds |

**Response:**

200 OK

### Adjusting Volume

Set system volume

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=setPlayerCmd:vol:50`

`command`: setPlayerCmd:vol <volume>

**Parameters:**

| Parameter | Description                         |
| --------- | ----------------------------------- |
| :vol      | Direct volume, value range is 0-100 |
| --:       | Decrease by 6                       |
| %2b%2b    | Increase by 6                       |

**Response:**

200 OK

### Mute and Unmute

Toggle mute for the device

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=setPlayerCmd:mute:<mute>`

`command`: setPlayerCmd:mute <mute>

**Parameters:**

| Parameter | Description       |
| --------- | ----------------- |
| `mute`    | Set the mute mode |
|           | `0`: Not muted    |
|           | `1`: Muted        |

**Response:**

200 OK

### Preset Content

Play Instruction for one of the Programmable Presets (maximum 12)

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=MCUKeyShortClick:<num_value>`

`command`: setPlayerCmd:mute

**Parameters:**

| Parameter   | Description                              |
| ----------- | ---------------------------------------- |
| `num_value` | The numeric value of the required Preset |
|             | Value range is from 0 - 12               |

**Response:**

200 OK


