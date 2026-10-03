# Troubleshooting-Wi-Fi-Connection-Problems-
A practical guide to diagnosing slow or missing internet, router faults, DNS problems and common connection error

Prepared by: Armstrong Francis Ogbonnaya
armstrongogbonnaya.official@gmail.com
Date: March 2025

1. Purpose and Scope
Few things interrupt a working day as quickly as a Wi-Fi connection that has stopped cooperating. This guide sets out
a sensible order for finding out what has gone wrong, beginning with the quick checks that clear up most problems and
moving on to the more technical ones. It is written for home users and small-office staff, and no networking background
is assumed. Where commands differ between Windows and macOS, both are given.
One habit will save you a lot of time: change only one thing at a time and test after each change. If you change three
settings at once and the connection returns, you will not know which one fixed it, and you will be stuck again the next
time it happens.

2. Five Quick Checks Before You Begin

a. Is it one device or all of them? Try a phone and a laptop on the same network. If only one device is affected, the
fault is most likely on that device and not on the router.

b. Is Wi-Fi really on? Make sure Airplane Mode is off and that the device is joined to the correct network, not a
neighbour's open one or a guest network.

c. Read the router lights. A steady power light and a steady internet (or globe) light are what you want. A red,
orange or blinking internet light usually means the router cannot reach your provider.

d. Try a cable. Connect a computer to the router with an Ethernet cable. If the wired connection works and Wi-Fi
does not, the trouble is on the wireless side only.

e. Move closer. Test beside the router. Thick walls, floors, mirrors and metal cabinets weaken the signal far more
than most people expect.

3. Match the Symptom to the Likely Cause

Use the table below to decide which section of this guide deserves your attention first.
What you notice
Likely cause
Go to
Connected to Wi-Fi, but “No internet” on
every device
Provider outage, or the router has lost its line to the provider

Sections 4 and 5

Pages load slowly; video keeps buffering
Some sites open, others say “server not
found”
One device will not connect while others are
fine
Wi-Fi keeps dropping or the network
disappears
Weak signal, interference, too many devices, or large
background downloads

DNS problem
Corrupted saved network profile or device settings
Overheating, interference, or outdated router firmware

Section 4

Section 6

Section 7

Section 5


4. Diagnosing Slow or No Internet

4.1 Measure before you guess

Run a speed test (fast.com or speedtest.net) standing next to the router, then run it again in the room where the
problem occurs. Compare both results with the speed you pay for. If the result beside the router is far below your plan,
the fault lies between the router and your provider. If it is fine beside the router but poor in the other room, the cause is
signal strength or interference.

4.2 Use ping to find where the connection breaks
Open Command Prompt (Windows) or Terminal (macOS) and run the three tests below in order. Your router’s address
is shown as the “Default Gateway” when you type ipconfig on Windows, or under Network settings on a Mac. It is
commonly 192.168.1.1 or 192.168.0.1.
Command
What it tests
If it fails
ping 192.168.1.1
The link between your device and the
router
The connection is fine but DNS is not working

(see Section 6)
The problem is local: Wi-Fi signal, device
adapter, or the router itself
ping 8.8.8.8
ping google.com
Whether the internet can be reached
without using DNS
Whether names can be translated into
addresses

The router is not getting through to your
provider (see Section 5)
Also watch the reply times. Consistently high values (above roughly 100 ms) or any lost packets point to congestion or
a weak signal rather than a complete failure.

4.3 Common reasons for a slow connection

• Congestion. Streaming, game downloads, cloud backups and system updates can quietly use most of your
bandwidth. Pause them and test again.

• Interference. The 2.4 GHz band is shared with neighbouring networks, microwave ovens and Bluetooth devices. If
your router supports 5 GHz, use it for devices that are close by. On 2.4 GHz, channels 1, 6 and 11 are the safest
choices.

• Distance and obstacles. If a room is simply too far away, a mesh system or a wired access point will do more than
any setting change.

• Your provider. Speeds can fall at peak hours or during maintenance. If a wired test is also slow, the cause is not
your Wi-Fi.

5. Router and Modem Issues

5.1 Restart in the right order

Switch off and unplug the router (and the modem, if you have a separate one) for at least 30 seconds. Power the
modem on first and wait about two minutes for its lights to settle, then switch on the router. Doing it in this order lets the
router receive a fresh connection from the modem instead of starting without one.

5.2 Check the physical connections

Make sure every cable is seated firmly and undamaged. The cable from the modem or wall socket should sit in the port
marked WAN or Internet, not in one of the numbered LAN ports. This is a surprisingly common mistake after a router
has been moved or replaced.

5.3 Look at the router’s status page

Type the router’s address into a browser and sign in with the details printed on the sticker underneath the unit. On the
status page, look for the WAN (or Internet) IP address. If it is blank or shows 0.0.0.0, the router is not receiving a
connection from your provider, and a call to them is the next step.

5.4 Firmware, placement and heat

Install any available firmware update from the admin page. Place the router in a central, raised position away from
metal objects and other electronics, and leave space around it for ventilation. A router that is hot to the touch will often
drop connections until it cools down.

5.5 Factory reset: the last resort

Hold the recessed reset button for about ten seconds. This erases all settings, including your Wi-Fi name, password
and any login details your provider supplied (for example, PPPoE credentials). Write these down before you reset.


6. DNS Problems
DNS works like a phone book for the internet: it turns a name such as google.com into the numeric address your
device needs. When it fails, you may see messages such as “server not found” or
DNS_PROBE_FINISHED_NO_INTERNET, even though ping 8.8.8.8 succeeds. Work through these steps in
order.

a. Flush the DNS cache. Windows: ipconfig /flushdns. macOS: sudo dscacheutil -flushcache; sudo
killall -HUP mDNSResponder.

b. Renew the IP address (Windows). Run ipconfig /release followed by ipconfig /renew.

c. Switch to a different DNS server. Good public options are Cloudflare (1.1.1.1 and 1.0.0.1) and Google
(8.8.8.8 and 8.8.4.4). On Windows go to Settings > Network & Internet > Wi-Fi > Hardware properties > DNS
server assignment > Edit. On macOS go to System Settings > Network > Wi-Fi > Details > DNS.

d. Test the result. Run nslookup google.com. A returned address means DNS is working again.

e. Rule out software. Temporarily turn off any VPN, proxy or security tool that filters traffic, and try a different
browser.

7. Common Connection Errors
Message or behaviour
What it usually means

“Can’t connect to this network”
“Incorrect password” or
authentication error

The saved network profile is corrupted,
or the adapter has glitched

Wrong key, or a security mode the
device does not support

What to try

Choose Forget network, restart the device,

then join again with the password

Retype the password carefully (it is
case-sensitive). 

Confirm the router uses

WPA2 or WPA3

“Connected, no internet” or

“Limited connectivity”

Stuck on “Obtaining IP address”

“IP address conflict”

Everything seems correct but
nothing loads (Windows)

The device has no valid address, or

the router has no route to the internet

The router’s DHCP service is not
handing out addresses

Two devices have been given the
same address

Corrupted network stack

8. When to Contact Your Internet Provider
Restart the router, renew the IP address,
then check the WAN status (Section 5.3)
Restart the router and confirm DHCP is
enabled in its settings
Restart the router and set the devices to
obtain an address automatically
Run Command Prompt as administrator:
netsh winsock reset and netsh int
ip reset, then restart
Some faults cannot be fixed from your side of the wall. Call your provider if the router’s WAN address is blank, the
internet light stays red or off, the problem also affects a wired connection, or speeds measured with a cable remain
well below your plan after a restart.

To save time on the call, have the following ready: the router model, the state of each light, the tests you have already
run, and the time the problem started. Keep a short written log of what you tried and what happened. It makes the
support conversation quicker and gives you a record if the fault returns.

Quick summary: check whether one device or all are affected, then use the three ping tests to see where the
connection breaks. Fix the router first, then DNS, then the individual device, testing after every change.
Questions or feedback? Contact Armstrong Francis Ogbonnaya at armstrongogbonnaya.official@gmail.com.
