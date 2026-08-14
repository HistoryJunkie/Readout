# readout

Live at https://historyjunkie.github.io/Readout/

This is a personal dashboard I built to see exactly what a browser can pull about me, my device, and my network, without me having to guess. Everything runs client side. Nothing gets logged or sent anywhere except two lookups for public IP and rough IP location, both fetched straight from ipapi.co so the network panel has something to show.

## What it shows

Browser info like user agent, language, cookies, automation flags.

Display info like resolution, pixel ratio, color depth, refresh rate.

Hardware info like CPU cores, memory, GPU renderer and vendor, WebGL details.

Network info like connection type, public IP, ISP, and a check for private IP leaks through WebRTC. The local network panel splits out real private IPs, like ones starting with 10 or 192.168, from public IPv6 addresses, since only the private ones count as an actual leak beyond what the site already sees from the request itself.

Time and locale info like timezone and offset, plus a button to request precise GPS location.

Storage info like what is available in local storage, session storage, and cookies currently set.

Sensors and permissions like battery status and camera, mic, geolocation permission states, all gated behind buttons since browsers require a user action for those.

About you, a plain language summary that pulls together region guesses, device class, and whether your IP based timezone matches your device timezone, which can hint at a VPN or proxy.

## Tracked live, no prompt required

This is the part that works the same way a tool like FullStory does. None of it needs permission, it just starts collecting the moment the page loads.

Session behavior. Time on page, mouse distance traveled, clicks, scroll depth, tab switches, idle time, keystroke count, and copy or paste events.

Interaction signals. Rage click detection, which is three or more clicks in about a second within a small radius of each other. There is a sandbox button on the panel that stalls for a second and a half so you can trigger one on purpose and watch it get caught, complete with a flash at the click point. There is also a sandbox text field that tracks focus count, dwell time, keystroke count, backspace count, pastes, and whether the field was focused and abandoned with no input. The actual characters typed are never captured, only the timing and counts.

Silent signals. Ad blocker detection, installed speech voices, WebGL extension count, client hints, resources loaded, pointer and hover capability, gamepad count, and whether the page is running as an installed app.

Canvas and font fingerprint, used to show how a browser can be re identified across visits without cookies.

## Privacy note

There is no export feature and no single object collecting everything into one place. Every panel reads and displays its own data independently. Reload the page and all of it is gone. NOTHING IS LOGGED OR SAVED!

## Notes

Some fields will say not exposed or n dot a depending on the browser. That is usually a real browser restriction, not a bug. Device memory and JS heap size are Chrome only for example.
