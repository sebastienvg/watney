# Watney Rover
Watney is a low-cost, open source, Raspberry Pi-enabled telepresence rover made of readily available parts.
Non-electronic parts of Watney are 3D printable.
Watney provides a low-latency HD video feed as well as bi-directional audio.
Watney uses a wireless charging dock with passthrough charging so it can be left on indefinitely.

Watney uses the [Janus WebRTC Server](https://janus.conf.meetecho.com/) and [Raspberry Pi Turnkey](https://github.com/schollz/raspberry-pi-turnkey) 
 

# Components
Head over to [Bill of Materials](BOM.md) for a list of components you need to purchase to build your own Watney. You'll also need a 3D printer, some PETG / Tough PLA as well as TPU filament. Lastly, you'll need a soldering iron and some wires, though most connections are made using standard breadboard jumper wire.


# Assembly
Detailed [assembly instructions](ASSEMBLY.md) can be found here. One of the goals of developing Watney is to make it easy to assemble - like IKEA furniture of electronics. Go slow and double-check your work. Take extra caution not to reverse polarity when hooking up components, as most of them will burn out if hooked up in reverse. You'll be working with LiPol batteries - please be careful not to puncture or short them, as they can become a fire hazard if used improperly. **You assume all responsibility for damages that may be caused by your Watney, whether it's assembled correctly or otherwise.**

# Configuration
Upon startup, Watney will detect if it's connected to a Wi-Fi hotspot. If not, it will host its own hotspot "Watney4".
Once you connect to the hotspot, you can control it directly by going to https://192.168.4.1:5000, or connect it to a Wi-Fi
hotspot by going to http://192.168.4.1

Default SSH credentials for Watney are pi / watney4. Watney's mDNS name is watney4.local.

Watney's configuration can be found in ~/watney/rover.conf:
* If you want to use different GPIO pins, you can specify them here
* If you find motors on either side running in reverse (backwards when it's supposed to be rotating forward) simply swap ForwardPin 
and ReversePin
* Restart your Watney for configuration changes to take effect

# Remote Access
Watney has no authentication / security. If you'd like to set it up for remote access, I recommend using [Zerotier](https://www.zerotier.com/). Adding Watney and your client computer to the same Zerotier network will make it appear as if they are on the same local network.

# Troubleshooting
* If you find your Watney randomly restarting when you move the camera, that means that the servo is drawing too much power from the Raspberry Pi. You can hook up the amplifier to one of the 3V outputs of the power board instead, and power the servo from the 5V output that was previously used by the amplifier.
* Watney works best with Chrome. Other browsers may not work well, or at all.
* Feel free to file an issue on GitHub if you have questions!

# Future Improvements
* **Better browser compatibility.** There's no reason it can't work in all major browsers.
* **Mobile-optimized control.** You'll be able to control your watney from your phone / tablet, especially in tandem with Remote Access.
* **Better volume scaling.** The volume slider is only usable at the top range - anything below 70% is barely audible. The slider should be scaled to control only the usable range instead.

