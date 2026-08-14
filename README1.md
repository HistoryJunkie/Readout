readout

Live at https://historyjunkie.github.io/Readout/

This is a personal dashboard I built to see exactly what a browser can pull about me, my device, and my network, without me having to guess. Everything runs client side. Nothing gets logged or sent anywhere except two lookups for public IP and rough IP location, both fetched straight from ipapi.co so the network panel has something to show.

What it shows

Browser info like user agent, language, cookies, automation flags.

Display info like resolution, pixel ratio, color depth, refresh rate.

Hardware info like CPU cores, memory, GPU renderer and vendor, WebGL details.

Network info like connection type, public IP, ISP, and a check for private IP leaks through WebRTC.

Time and locale info like timezone and offset, plus a button to request precise GPS location.

Storage info like what is available in local storage, session storage, and cookies currently set.

Sensors and permissions like battery status and camera, mic, geolocation permission states, all gated behind buttons since browsers require a user action for those.

Session behavior tracked live the whole time the page is open. Time on page, mouse distance traveled, clicks, scroll depth, tab switches, idle time, keystroke count, and copy or paste events. This part needs no prompt at all, same category of tracking a tool like FullStory does.

Silent signals that also need no prompt. Ad blocker detection, installed speech voices, WebGL extension count, client hints, resources loaded, pointer and hover capability, gamepad count, and whether the page is running as an installed app.

Canvas and font fingerprint used to show how a browser can be re identified across visits without cookies.

Privacy note

There is no export feature and no single object collecting everything into one place. Every panel reads and displays its own data independently. Reload the page and all of it is gone.

Setup

Clone or download this repo. Rename the html file to index.html if it is not already. Push to a GitHub repo. Go to Settings then Pages. Set source to deploy from a branch, branch main, folder root. Save and wait about a minute. The site will be live at your GitHub Pages URL over HTTPS, which is required for the permission gated panels like geolocation and camera or mic labels to actually work.

Local option

Run a simple server from the folder, for example python3 -m http.server, then open it from other devices on the same network using that machine's local IP. Permission gated panels will not work this way outside of localhost since they need a secure context.

Notes

Some fields will say not exposed or n dot a depending on the browser. That is usually a real browser restriction, not a bug. Device memory and JS heap size are Chrome only for example. The WebRTC leak check separates private IPs like ones starting with 10 or 192.168 from public IPv6 addresses, since only the private ones count as an actual leak beyond what the site already sees from the request itself.
