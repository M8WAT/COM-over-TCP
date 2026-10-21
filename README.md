# COM-over-TCP
Batch files used to share (on-demand) COM Port over TCP to allow remote control of Amateur Radio Antenna Rotater


## How it Works

Simply, hub4com.exe from the com0com project on sourceforge: https://sourceforge.net/projects/com0com/


## Server Side (Where the Serial Device is Connected)

Download hub4com.exe and server-side.bat, to C:\hub4com\

Amend the batch file as required. In my setup, the serial device is on COM2 and hub4com opens TCP port 7000.

The batch file contains an argument (--share-mode=on) that keeps the COM port closed until a remote client connects. This means that the COM port can continue to be used locally, whilst still "listening" for a remote client.

Note: only 1 user can utilise the serial device at one time.

Create a desktop shortcut aimed at C:\hub4com\client-side.bat

### Optional but Recommended - On Boot Task Scheduler

Rather than using the batch file, download the Task Scheduler Template - 'COM over TCP - COM2.xml'

Open Task Scheduler and import the template: \
&emsp; Open Action Menu \
&emsp; Select Import Task \
&emsp; Select the Template File

Amend details as necessary: \
&emsp; General - Name (of task), User, etc. \
&emsp; Actions - edit the arguments and ensure the COM port and TCP port numbers are as required

When complete, click OK. If you haven't changed the 'General' option to allow running without login - required for unattended operation (and convenience) - you will be asked to enter your password to allow this.

## Client Side (Remote Machine Where Access is Required)

Download and install com0com and download hub4com.exe and client-side.bat to C:\hub4com\

Once installed, add a Virtual Port Pair. Under CNCA0, tick 'use Ports class'. This will setup a 'physical' COM port - e.g. COM6 - where you point your desired software / application to connect to your remote serial device, and a Virtual Serial Port - CNCB0

Amend the batch file as required. In my setup, the Virtual Serial Port is CNCB0 and hub4com connects on TCP port 7000 at server address 100.64.0.101

Create a desktop shortcut aimed at C:\hub4com\client-side.bat


## Security Reommendation

If you plan to use your serial device over the internet, I would recommend using Tailscale, Netbird or other VPN solution. I would highly discourage exposing your serial device directly to the internet (usually by NAT port forwarding in your router).
