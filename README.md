# argosmock

https://mail-attachment.googleusercontent.com/attachment/u/0/?ui=2&ik=d95df0d3b9&attid=0.2&permmsgid=msg-f:1660425260019844401&th=170b03fa07918531&view=att&disp=inline&realattid=170b039ac18af1319ce3&saddbat=ANGjdJ8mZpu-zSpsl9DsbWT-4DWFUxd6_MUwNU5Q-ZSk06cswBUCVdaB7HTvaH8Qms8YdEEWqG5s5_V1KM1yp-mQim00SiF5DAXL_9Pm9HGdZaSIj31V0aYaccntOYPDU3XsH-Hp_9BobhAXumOqBxiNso-jgGDhwD1aOVu_QBsFUqToE1gDi2-CWAIJJMQY4mJlJ3Vu4g0RAhnMup98TmZe5rJ_oT_uDnnXJR7jbwWST-cu8zCgilxl6sv_MCzZIEHdVlt-hLlP4vqEf9S9XqlbhQHX1hd1DhSXZNhsuvw068uoFMAOzYdz9pwA12cgaPtyl0VDP8g6GcsqW0uXvrfQafecA-FWCz-HZ6vp5zz6K14sIBnDgRvrzGBrAh84In8ubWnnI1ffc5OL3J1Y_iVmUONQslz2KeJ1_953D69uihAgdMzZzyGaHKf6I0AcXyc4pD0uzg0im67bgil7RjVGmpAzhe5ec70QlqK0ACi_4maFIYRjUOmHcQJExrN_zhvGBId-ws32EwHwA1WLotoOhC50c3-BE9N5DIYJkBz1F_lsansCz-tNalzUCkK0SdlxLyJ6byU-4lLZadEQtvtCFApL77gB2Canzs0Oe1q6LugPLfLhHQKfmJuPC71P49PrjO6lfJLZfsvIxNNGbkbHnCgC2TfhiOysWJAdh6mfyRclIeYca0pF7X3FZ00

---------------------------------------------

GetDeviceInfo
URL: http://<IP_of_Argos>/device/info
Argos FW v0.0.1 supprots GetDeviceInfo API to show the status of Argos Pre-EV sample.
Currently only selected parameters are supported in FW v0.0.1.
The unsupported parameters are colored with Grey. 

brand “VZC” String
type “USA” String
model “VCAM-D-1000” String
hardwareVersion “SGA0.0” String
mac2_4Address XXXXXXXXXXXX String
mac5_0Address Same as mac2_4Address String
BTmacAddress Not Supported String
coreFirmware “0.0.1.0” String
sdCardId XXXXXXXXX String
sdCardSize In MB Size String
sdCardAvailableSpace In MB Size String
serialNumber SN10000000XX String
pseudoIMEI Dummy Hex String
wifiBand 2.4G or 5G String
ssid SSID String
hotspotSerialNumber Not Supported String 
hardwareVersion “SGA0.0” String


-----------------------------------------------

SetWiFiClientMode
URL: http://<ip_of_argos>/eng/SetWiFiClientMode
Set Dashcam in paired mode. Dashcam will transfer from unpaired mode to paired mode with
and try to connect device on with given SSID and Passphrase on 2.4 G band. Currently only
plaintext ssid and passphrase are supported. The payload is in JSON format.

{
“ssid”: “yourssid”,
 “passphrase” : “yourpass”
} 

------------------------------------------------

SetDevSetting
URL: http://<ip_of_argos>/eng/SetDevClientMode
Engineering Testing API for Device modification. The configurable setting could be any
combination of keys in following table. However, when applied a reboot is needed to validate
the new settings on FW v0.0.1.
Here is a example which will change device in to STA mode on 5G band with new ssid and
password.


{
 “deviceMode” : “paired”,
 “wifiBand” : “5G”,
 “wifissid” : “wifissid”,
 “wifipassphrase” : “wifipass”
} 


IoTGatewayIP “IoTGatewayIP” IP address IP Address of IotGateway
IoTGatewayPort “IoTGatewayPort” Int IP Port of IotGateway
VideoPlatReqURL
“VideoPlatReqURL” URL string URL for Video Upload
Request
MessageTimout “MessageTimout”
Int Timeout of Message
resending
ApiUrl “ApiUrl” string Restful API default URL
NTP Server “NTPServ” DomainName String NTP Server Address
Heartbeat Period “Heartbeat Period” Int Heartbear period 


--=--------------------------------------------------




Heartbeat
Argos FW v0.0.1 supports heartbeat info with configurable period (default 15 seconds).
Not all status are monitored in FW v0.0.1. Only Bit 0, Bit 12,Bit 13, Bit 14, and Bit 21 are
supported in current FW.
Bit 0: 1 = forward-facing camera is recording
Bit 1: 1 = forward-facing camera functional
Bit 2: 1 = forward-facing camera commanded off
Bit 3: 1 = inward-facing camera is recording
Bit 4: 1 = inward-facing camera functional
Bit 5: 1 = inward-facing camera commanded off
Bit 6: 1 = ambient light level high
Bit 7: 1 = IR LEDs on
Bit 8: 1 = IR LEDs functional
Bit 9: 1 = indicator LEDs commanded off
Bit 10: 1 = inertial module functional
Bit 11: 1 = inertial module calibration completed
Bit 12: 1 = SD card inserted
Bit 13: 1 = SD card full (less than 1% of
capacity is free)
Bit 14: 1 = SD card functional
Bit 15: 1 = thermal slowdown
Bit 16: 1 = non-volatile memory bank 1
corrupted
Bit 17: 1 = non-volatile memory bank 2
corrupted
Bit 18: 1 = program memory bank 1 corrupted
Bit 19: 1 = program memory bank 2 corrupted
Bit 20: 1 = RTC has valid time
Bit 21: 1 = time synchronized with VTU since wake ( Default NTP server is ntp.pool.org) 

