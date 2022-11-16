# Radxa zero power consumption figures
Power consumption measurements for the [Radxa zero SBC](https://wiki.radxa.com/Zero), plus whatever other info on it that people might desire but is not available on the wiki yet.

## Power consumption figures from tests

### Current @5V, for many use cases
situation | current (min - max)
--------- | -------
(**BASELINE**) idle, wifi off | 110mA - 120mA
idle, wifi on | 100mA - 160mA
youtube video, 720p, browser | 190mA - 270mA
youtube video, 720p, browser, CPU speed locked @1.8GHz | 220mA - 370mA
1080p h264 video from `yt-dlp` to `mpv` | 280mA - 400mA
(**SIMULATED MAXIMUM**) wifi saturated with `iperf3` and CPU full-load stress test |  550mA
720p h264 video from `yt-dlp` to `mpv` | 220mA - 240mA
720p h264 video playback on `mpv`, wifi off | 160mA to 250mA
wifi download @ 400KB/s | 120mA - 220mA
1080p 60fps video on `mpv`, wifi off | 310mA - 350mA

### Current vs clock speed running 1080p video offline
![radxa current draw from 5V supply vs locked clock-speed](https://github.com/PhiCross5/RadxaZero-powerConsumption/raw/main/radxa-consumption-graph.png)
