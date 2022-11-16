# Radxa zero power consumption figures
Power consumption measurements for the [Radxa zero SBC](https://wiki.radxa.com/Zero), plus whatever other info on it that people might desire but is not available on the wiki yet.

## Power consumption figures from tests

### TLDR (Too Long, Didn't Read) plus some key facts
With 5V power supply:
- **Idle consumption is 100mA**, regardless of clock speed.
- **Maximum power consumption is 550mA**.
- Sleep mode might make idle power lower, but my particular configuration didn't support that.
- **Connected but idle Wifi consumes 40mA**. This is for just the WiFi module.
- **Fully loaded Wifi consumes 180mA**
- Hardware acceleration of video encoding/decoding is not supported yet, so the power consumption in that use case might become dramatically lower in the future.
- **A 5000mAh powerbank will power it for at least 5.5h, at most 36h**. You could build a smartphone or tablet with it, if you don't mind needing a slightly bigger battery.
- Lastly, for the inspector types, i'll have you know i was running the latest Manjaro ARM, Plasma variant, with display output enabled. The 7-inch LCD i was using had maximum brightness but it was not running on the same power rail, so it doesn't affect the power consumption readings.

### Current @5V, for many use cases
situation | current (min - max)
--------- | -------
(**BASELINE**) idle, wifi off | 110mA - 120mA
idle, wifi on | 100mA - 160mA
youtube video, 720p, browser | 190mA - 270mA
youtube video, 720p, browser, CPU speed locked @1.8GHz | 220mA - 370mA
1080p h264 video from `yt-dlp` to `mpv` | 280mA - 400mA
(**SIMULATED MAXIMUM**, tested by *Rauxon* at Radxa discord) wifi saturated with `iperf3` and CPU full-load stress test |  550mA
720p h264 video from `yt-dlp` to `mpv` | 220mA - 240mA
720p h264 video playback on `mpv`, wifi off | 160mA to 250mA
wifi download @ 400KB/s | 120mA - 220mA
1080p 60fps video on `mpv`, wifi off | 310mA - 350mA

### Current vs clock speed running 1080p video offline
The 4 x Cortex A53 @ 1.8GHz on the S905Y2 cannot decode 1080p60 video at full-speed (And it shouldn't have to, there's a specialized "Video Processing Unit" for that), thus doing such operation at different clock speeds can serve as an estimate of maximum power consumption of the CPU, not accounting for Wireless activity.
![radxa current draw from 5V supply vs locked clock-speed](https://github.com/PhiCross5/RadxaZero-powerConsumption/raw/main/radxa-consumption-graph.png)
