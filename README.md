# RPI_something
About raspberry pi's note

### CPU Temperature
#### 1. cat
```
cat /sys/class/thermal/thermal_zone0/temp
```
此數字除以1000 就是攝氏溫度
```
echo "Temperature: $[$(cat /sys/class/thermal/thermal_zone0/temp)/1000] °C"
```
thermal_zone0 代表設備
```
cat  /sys/class/thermal/thermal_zone0/type
```
---
#### 2. vcgencmd
```
vcgencmd measure_temp
```
其他項目:
時脈頻率（clock frequency）
```
vcgencmd measure_clock <clock>
```
\<clock>=arm、core、h264、isp、v3d、uart、pwm、emmc、pixel、vec、hdmi、dpi。
```
for src in arm core h264 isp v3d uart pwm emmc pixel vec hdmi dpi ; do echo -e "$src:\t$(vcgencmd measure_clock $src)" ; done
```
電壓（voltage）
```
vcgencmd measure_volts <id>
```
\<id>=core、sdram_c、sdram_i、sdram_p
```
for id in core sdram_c sdram_i sdram_p ; do echo -e "$id:\t$(vcgencmd measure_volts $id)" ; done
```
Codec
```
vcgencmd codec_enabled <codec>
```
\<codec>=H264、MPG2、WVC1、MPG4、MJPG、WMV9。
```
for codec in H264 MPG2 WVC1 MPG4 MJPG WMV9 ; do echo -e "$codec:\t$(vcgencmd codec_enabled $codec)" ; done
```
---
查看 vcgencmd 所有可用的參數:
```
vcgencmd commands
```


