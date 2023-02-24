# Malicious App for Android

In this report, we have shown how we can hack an android mobile device using MSF
venom and the Metasploit framework. We will use MSF venom for generating the
payload, save it as an .apk file and set up a listener to the Metasploit framework. Once
the user/victim downloads and install the malicious .apk, an attacker can easily get back
the session on Metasploit. To accomplish this, an attacker needs to do some social
engineering to install the .apk on the victim’s mobile device.

The payload successfully penetrated the Android device using Kali Linux and penetration testing tools(Metasploit).
Successful creation and deployment of virus for android injected with payload in the form of an android app. With the help of our malicious .apk file (virus app for android) named Notes(apk).

Metasploit Framework--
 Metasploit is a penetration testing framework that makes hacking simple. It's an
essential tool for many attackers and defenders. Point Metasploit at your target,
pick an exploit, what payload to drop, and hit Enter.
 Better still, the core Metasploit Framework is both free and libre software and
comes pre-installed in Kali Linux. (It's BSD-licensed). The framework offers only a
command-line interface, but those wanting GUI-based click-and-drag hacking —
plus some other cool features — can drop a bundle for per-seat licenses
to Metasploit Pro.
Meterpreter--
 Meterpreter is an advanced, dynamically extensible payload that uses in-memory DLL
injection stagers and is extended over the network at runtime. It communicates over
the stager socket and provides a comprehensive client-side Ruby API. It features
command history, tab completion, channels, and more.
 Metepreter was originally written by skape for Metasploit 2.x, common extensions
were merged for 3.x and is currently undergoing an overhaul for Metasploit 3.3. The
server portion is implemented in plain C and is now compiled with MSVC, making it
somewhat portable. The client can be written in any language but Metasploit has a
full-featured Ruby client API.
 The target executes the initial stager. This is usually one of bind, reverse, findtag,
passivex, etc.
 The stager loads the DLL prefixed with Reflective. The Reflective stub handles the
loading/injection of the DLL.
 The Metepreter core initializes, establishes a TLS/1.0 link over the socket and sends a
GET. Metasploit receives this GET and configures the client.
 Lastly, Meterpreter loads extensions. It will always load stdapi and will load priv if the
module gives administrative rights. All of these extensions are loaded over TLS/1.0
using a TLV protocol.
Msfvenom--
 MSFvenom is used to make a payload to penetrate the Android emulator. Note: In
this command, we have used the local address because we are demonstrating in the
local environment. To perform in the public network, you should enter your public
address in LHOST and enable port forwarding on the router.
 Msfvenom is a command line instance of Metasploit that is used to generate and
output all of the various types of shell code that are available in Metasploit.
 Reverse TCP Payload
 A reverse shell (also known as a connect-back) is the exact opposite: it requires the
attacker to set up a listener first on his box, the target machine acts as a client
connecting to that listener, and then finally the attacker receives the shell.
It is a combination of MSFpayload and MSFencode. These tools are extremely useful for
generating payloads in various formats and encoding these payloads using various
encoder modules. 



What are we going to do?

Using Metasploit Framework and MSF venom we are going to create a malicious .apk file.
The .apk file will be having a particular payload and will have all file necessary to get access
to various features of the target device. The .apk will be sent to the victim’s device using a
link which will automatically initiate the download of the the malicious .akp file into the
device. The .apk will ask the victim for allowance of features on the device. After victim
grants the access to the app we can start our MSF console and initiate a meterpreter
session which will become a means of transfer for victims data to the hacker.
After establishing a successful connection between the victim’s device and the hacker we
can accomplish huge number of tasks and gather enormous amount of victim’s data. 


How Are we going to do.
We will demonstrate this by using the following tools
 VirtualBox (virtual environment)
 Kali Linux
 Android device/emulator
We are using Kali Linux and an Android device to perform mobile penetration testing. Kali
Linux is one of the Debian-based operating systems with several tools aimed at various
information security tasks such as penetration testing, forensics and reverse engineering.
Kali Linux is one of the most-used operating systems for penetration testing. 
