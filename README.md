# readout

Live at https://historyjunkie.github.io/Readout/

This is a personal dashboard I built to see exactly what a browser can pull about me, my device, and my network, without me having to guess. Everything runs client side. Nothing gets logged or sent anywhere except two lookups for public IP and rough IP location, both fetched straight from ipapi.co so the network panel has something to show.

Every reading on this page is passive. Nothing here ever pops a permission prompt. That includes things like geolocation and camera or mic access on purpose, since those require asking, and this project is only meant to show what a page can gather without asking.

## What it shows

Browser info like user agent, language, cookies, automation flags.

Display info like resolution, pixel ratio, color depth, and a live measured screen refresh rate.

Hardware info like CPU cores, memory, GPU renderer and vendor, GLSL version, max viewport size, and WebGPU adapter details where supported.

Network info like connection type, downlink and RTT, public IP, ISP, and how many times the connection type has changed since the page loaded.

Local network info pulled from WebRTC and SDP candidate gathering. Shows whether a private IP is exposed separate from your public one, how many local network interfaces are visible, what candidate types were found, and whether a relay server is in play.

Time and locale info like timezone, UTC offset, locale, and calendar system.

Storage info like what is available in local storage, session storage, indexedDB, and cookies currently set on the page.

Sensors and permissions shown as current state only. Battery level, permission states for things like camera and microphone, and a count of media devices present without ever asking for their labels.

About you, a plain language summary that pulls together region guesses, device class, and whether your IP based timezone matches your device timezone, which can hint at a VPN or proxy.

Fingerprint surface, the signals that combine to re identify a browser across visits without cookies. Canvas hash, audio hash from an oscillator run through a compressor, DOM geometry hash from sub pixel rendering differences, and a font probe against common installed fonts.

Performance info like page load time, transfer size, JS heap usage where exposed, which protocol your resources loaded over, and average DNS, TCP, and TLS timing.

## Tracked live while the page is open

Session behavior. Time on page, mouse distance traveled, clicks, scroll depth, tab switches, idle time, keystroke count, and copy or paste events.

Interaction signals. Rage click detection, which is three or more clicks in about a second within a small radius of each other. There is a sandbox button that stalls for a second and a half so you can trigger one on purpose and watch it get caught, with a flash at the click point. There is also a sandbox text field that tracks focus count, dwell time, keystroke count, backspace count, average flight time between keys, average hold time per key, pastes, and whether the field was focused and abandoned with no input. The actual characters typed are never captured, only timing and counts. The same panel also tracks text selections by length and duration, never the selected text itself, and samples cursor speed to flag motion that looks unusually constant, which is one way automated browsers get caught.

Silent signals. Ad blocker detection, installed speech voices, WebGL extension count, client hints, resources loaded, pointer and hover capability, gamepad count, whether the page is running as an installed app, and a count of previously paired bluetooth or usb devices. That last one only returns devices already granted to this origin before, it cannot discover new ones or prompt for access.

## Privacy note

There is no export feature and no single object collecting everything into one place. Every panel reads and displays its own data independently. Reload the page and all of it is gone. Nothing here will ever ask you for a permission, and features that would have needed one, like precise location or camera and mic labels, were removed on purpose.

## Setup

Clone or download this repo. Rename the html file to index.html if it is not already. Push to a GitHub repo. Go to Settings then Pages. Set source to deploy from a branch, branch main, folder root. Save and wait about a minute. The site will be live at your GitHub Pages URL over HTTPS.

## Local option

Run a simple server from the folder, for example python3 -m http.server, then open it from other devices on the same network using that machine's local IP.

## Notes

Some fields will say not exposed or n dot a depending on the browser. That is usually a real browser restriction, not a bug. Device memory and JS heap size are Chrome only for example, and WebGPU adapter info depends on browser support. The WebRTC leak check separates private IPs, like ones starting with 10 or 192.168, from public IPv6 addresses, since only the private ones count as an actual leak beyond what the site already sees from the request itself.
