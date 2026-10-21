# COM-over-TCP
Batch files used to share (on-demand) COM Port over TCP to allow remote control of Amateur Radio Antenna Rotater


## How it Works

Simply, hub4com.exe from the com0com project on sourceforge: https://sourceforge.net/projects/com0com/


## Server Side (Where the Serial Device is Connected)

Download hub4com.exe and server.bat, to C:\hub4com\

Ammend the batch file as required. In my setup, the serial device is on COM2 and hub4com opens TCP port 7000.


## Client Side (Remote Machine Where Access is Required)

Download and install com0com and download hub4com.exe and client.bat to C:\hub4com\

Once installed, add a Virtual Port Pair. Under CNCA0, tick 'use Ports class'. This will setup a 'physical' COM port - e.g. COM6 - where you point your desired software / application to connect to your remote serial device.

Ammend the batch file as required. In my setup, the 'physical' serial port is COM6 and hub4com connects on TCP port 7000 at server address 100.64.0.101
