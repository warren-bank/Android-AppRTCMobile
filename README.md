#### [AppRTCMobile](https://github.com/warren-bank/Android-AppRTCMobile)

AppRTCMobile is:
* an example Android client for [https://appr.tc](https://appr.tc)
* an Android application using WebRTC Native APIs via JNI

#### Notes

* this example is copied from [the official WebRTC source code repo](https://webrtc.googlesource.com/src/+/49fa4ea0e7533cac190e32f3f7f2de3876385e82/examples/androidapp/)
  * commit: `49fa4ea0e7533cac190e32f3f7f2de3876385e82`
  * tag: `1.0.28513`
  * date: July 09, 2019
* minimum supported version of Android:
  * Android 4.1 (API level 16)

#### Links:

* [https://opensource.google/projects/webrtc](https://opensource.google/projects/webrtc)
* [https://webrtc.org/native-code/android/](https://webrtc.org/native-code/android/)
* [https://webrtc.googlesource.com/src/](https://webrtc.googlesource.com/src/)<br>[https://webrtc.googlesource.com/src/+/master/examples/androidapp/](https://webrtc.googlesource.com/src/+/master/examples/androidapp/)

- - - -

#### Direct connection on LAN

Step-by-step instructions for initiating a video call between 2 devices on the same local area network (LAN) without requiring any external server(s):

* connect 2 devices to the same LAN
  - example:
    * IP of device &#x23;1: `192.168.1.10`
    * IP of device &#x23;2: `192.168.1.20`
* launch `AppRTCMobile` on both devices
* on device &#x23;1:
  - connect to room: `0.0.0.0:8888`
    * effect:
      - `ConnectActivity` starts `CallActivity`
      - `CallActivity` runs `DirectRTCClient`
      - `DirectRTCClient` runs `TCPChannelClient`
      - `TCPChannelClient` runs `TCPSocketServer`
* on device &#x23;2:
  - connect to room: `192.168.1.10:8888`
    * effect:
      - `ConnectActivity` starts `CallActivity`
      - `CallActivity` runs `DirectRTCClient`
      - `DirectRTCClient` runs `TCPChannelClient`
      - `TCPChannelClient` runs `TCPSocketClient`
      - `TCPSocketClient` connects to `TCPSocketServer` on device &#x23;1
        * server sends SDP offer
        * client accepts
        * WebRTC video call directly connects both devices on LAN

- - - -

#### Legal:

* Copyright: The WebRTC project authors. All rights reserved.
* [LICENSE](https://webrtc.googlesource.com/src/+/49fa4ea0e7533cac190e32f3f7f2de3876385e82/LICENSE)
