## Ubuntu PPA
https://launchpad.net/~rsatom/+archive/ubuntu/gst-rtsp-server-1.0  
*At the moment it contains only binaries for Ubuntu 17 (Artful)*

## MODE_PLAY | MODE_RECORD Demos

### RtspRestreamServer

https://github.com/RSATom/RtspRestreamServer

### `videotestsrc` restreaming

```
                           +----------------------------------------------------------------------+
                           |                             gst-rtsp-server                          |
                           |(videotestsrc pattern=smpte100 ! x264enc ! rtph264pay name=pay0 pt=96)|
                           +----------------------------------------------------------------------+
                                                               ^
                                                               |
                                                           RTSP PLAY
                                                               |
                                                       +--------------+
                                                       | Raspberry Pi |
                                                       +--------------+
                                                               |
                                                          RTSP RECORD
                                                               |
                                                               v
                   +--------------------------------------------------------------------------------------+
+-----+            |                                  gst-rtsp-server                                     |
| You |-RTSP PLAY->|(rtph264depay name=depay0 ! h264parse ! rtph264pay config-interval=-1 pt=96 name=pay0)|
+-----+            |                                                                                      |
                   +--------------------------------------------------------------------------------------+
```

`rtsp://restream-basic.eastasia.cloudapp.azure.com:8100/bars`

### D-Link DCS-931L ip cam restreaming

```
+-----+              +-----------------+                +--------------+         +-----------------+
| You |--RTSP PLAY-->| gst-rtsp-server |<--RTSP RECORD--| Raspberry Pi |--HTTP-->| D-Link DCS-931L |
+-----+              +-----------------+                +--------------+         +-----------------+
```

`rtsp://restream-basic.eastasia.cloudapp.azure.com:8100/dlink931`

