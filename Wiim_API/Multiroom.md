## Multiroom

Multiroom is a very special feature in LinkPlay modules. Several devices can be grouped together to form a so-called listening zone, so that all devices in this group play music from one and the same source. The volume can be controlled per device or for the entire group.

If you have already grouped several devices into one zone, then one device of this group is always the host. All other devices are child to this one. This is important to know if you want to play music via Spotify Connect. In the Spotify app, only the host appears in the list of Connect devices! All other devices are hidden.

### Add Device to Multiroom Group

This command will add Device to the Host Device or an existing Multiroom Group (which is assigned to the host device). The command is sent to the Guest Device and the IP Address of Host Device needs to be added to the command as shown below.

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=ConnectMasterAp:JoinGroupMaster:eth<ip_address>`

`command`: ConnectMasterAp:JoinGroupMaster

 **Parameters:** 

| Parameter    | Description                                                |
| ------------ | ---------------------------------------------------------- |
| `ip_address` | The IP address of the host device to be added to the group |

**Response:**

200 OK

### Remove Device from MultiRoom Group

This command will remove the required Guest Device from the Multi-Room Group

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=multiroom:SlaveKickout:<ip_address>`

`command`: ConnectMasterAp:SlaveKickout

 **Parameters:** 

| Parameter    | Description                                                    |
| ------------ | -------------------------------------------------------------- |
| `ip_address` | The IP address of the host device to be removed from the group |

**Response:**

200 OK

### Request a list of Devices in a Multiroom

This command requests a list of Devices in the Multiroom Group

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=multiroom:getSlaveList`

`command`: ConnectMasterAp:getSlaveList

**Response:**

```json
{
    "slaves": 1,
    "wmrm_version": "4.2",
    "slave_list": [
        {
            "name": "WiiM Pro-DE2A",
            "uuid": "FF98F09C6AC7444E3A776C04",
            "ip": "172.17.130.113",
            "version": "4.2",
            "type": "WiiMu-AmlogicA1",
            "channel": 0,
            "volume": 100,
            "mute": 0,
            "battery_percent": 0,
            "battery_charging": 0
        }
    ]
}
```

**Value-Description**

| Key            | Value-Description                                                         |
| -------------- | ------------------------------------------------------------------------- |
| `slaves`       | The number of Guest Devices connected to this Host Device. Numeric value. |
| `wmrm_version` | !! DOCUMENTATION IN PROGRESS !!                                           |
| `slave_list`   | Identifier for the array of Guest Devices.                                |

**Value-Description (array)** 

| Key                | Value-Description                                                                                                        |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| `name`             | The name of the Guest Device                                                                                             |
| `uuid`             | UUID of the Guest Device                                                                                                 |
| `ip`               | Guest Device's IP address                                                                                                |
| `version`          | !! DOCUMENTATION IN PROGRESS !!                                                                                          |
| `type`             | Audio Module type `WiiMu-A31`: LinkPlay A31 (used for A50, PRO, MINI, S50+ AMP)                                          |
| `channel`          | Active audio channel `0`: Stereo `1`: Left channel `2`: Right channel                                                    |
| `volume`           | Current volume. Value range is from 0 - 100. So can be considered a linear percentage (0% to 100%)                       |
| `mute`             | Mute status: `0`: Guest Device is unmuted `1`: Guest Device is muted                                                     |
| `battery_percent`  | Battery level (if battery is present). Value ranges from 0 - 100. So can be considered a linear percentage (0% to 100%)  |
| `battery_charging` | Flag that indicates whether the battery is currently charging or not. `0`: Battery not charging `1`: Battery is charging |

**Example response when there are no Guest Devices connected e.g. This Device is in standalone mode:**

```json
{
   "slaves": 0,
   "wmrm_version": "4.2"
}
```

### Adjust Volume of a Slave Device

Allows you to adjust the volume of each Guest Device in a group. The request must be sent to the Host Device of the group. When a Guest Device is removed from the group (command `multiroom:SlaveKickout`), this volume level is overwritten an the Guest Device will return to its previous independent volume.

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=multiroom:SlaveVolume:<ip_address>:<num_volume>`

`command`: multiroom:SlaveVolume

 **Parameters:** 

## Parameters

| Key          | Value-Description                                                           |
| ------------ | --------------------------------------------------------------------------- |
| `ip_address` | The IP address of the child/slave media player to be removed from the group |
| `num_volume` | Volume level requested. Numeric value ranges from 0-100                     |

**Response:**

200 OK

### Mute a Slave Device

Mute a specific Slave Device of a Multiroom group.

**HTTP Method:** GET **Endpoint:** `/httpapi.asp?command=multiroom:SlaveMute:<ip_address>:<flag_mute>`
`command`: multiroom:SlaveVolume

 **Parameters:** 

| Key          | Value-Description                                               |
| ------------ | --------------------------------------------------------------- |
| `ip_address` | The IP address of the Guest Device to control with this command |
| `flag_mute`  | The desired mute status                                         |
|              | `0`: Unmuted                                                    |
|              | `1`: Muted                                                      |

**Response:**

200 OK
