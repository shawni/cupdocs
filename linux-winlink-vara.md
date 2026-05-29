# Linux Winlink Express + VARA FM

## Why?

1. Windows 10 off support, Windows 11 too tied to cloud + online
1. Good for training

## Process

1. Install Zorin OS 18 on computer, preferable i5+ with 8GB RAM, storage as
needed but at least 120GB - less CPU or RAM will function less well with VARA,
might be OK for other protocols.  "Telnet Winlink"/"Telnet Post Office" will
work with 4GB laptops.
1. Install Bottles- go to menu, "All" apps, scroll down to Windows
App Support and choose it.  You will need the root password to install
Bottles.  Close the software manager.
1. Run "Windows Apps/Bottles" from the start menu.  It will install a few
prerequisites from the Internet here.
1. Click "Start using Bottles", click on "hamburger" main menu icon on upper
right, pick Preferences.
1. On "General" menu, click off choices that confuses the experience.  I remove:
    1. Show Funding Dialog
    1. List Steam...
    1. List Epic...
    1. List Ubisoft..
1. Click "Runners" at the top.  Open "Caffe" menu, select download option next
to "Caffee 9.7".
1. Close Preferences.
1. Create New Bottle, name it "Winlink".  It's an "Application" type of
bottle.  Choose caffe-9.7 as the runner, then click "Create".
1. Bottle creation with these setting will download more compatibility items,
some DLLs and fonts.  Let it work a bit.
1. When the Bottle is created, click on the arrow ->.
Scroll down to dependencies.  Install "vbrun6" with the download button,
and also "vcredist2015".  These will help VARA display properly.

1. OPTIONAL: If your radio interface presents a serial port over USB, we have
to inform Bottles it exists and allow access to it.  THIS IS NOT NEEDED FOR
SIGNALINK.
    1. Go back to the "Details" window on your current bottle (back arrow at
top left) and select "Run Executable".  Acknowledge the fact that a Bottle is
 a sandbox environment.
    1. In the file selector, choose "drive_c", then "windows", then "regedit.exe".
    1. In regedit, add a String key under the path
 HKEY_LOCAL_MACHINE / Software / wine / Ports""".  The key is "COM1", and the
path is "/dev/ttyUSB0", assuming that's where it shows up on the Linux side.
It's very very likely so.
    1. Exit regedit.
    1. Exit Bottles.  You will need to start a Terminal.
    1. In Terminal, type "sudo usermod -a -G dialout :your-login-name:"  Please
substitute your actual login name there.  You will need to type in your
password for this step.
    1. Log out completely and log back in, or alternatively reboot your laptop,
to make sure the group changes are in effect.
    1. Restart Bottles.

1. Using the Brave web browser, download Winlink Express and VARA FM from
winlink.org, under the Download tab.  Winlink Express is under User Programs,
VARA FM is in VARA Products.
1. Open a Terminal, type:
"cd Downloads; unzip Winlink*.zip; unzip VARA*.zip; exit"
1. In Bottles, select the "winlinK" bottle and Run Executable (or just use
the gear icon in the Bottles list)
1. Select "Downloads" and then the VARA FM executable, and run it.
Configure it as you would normally.  Do not use the "PulseAudio" devices.
You may have to adjust volume for the device by accessing the volume
controls in the menu bar at the bottom of your screen.
1. Close VARA; choose "Run Executable" again.  This time pick the Winlink
Express executable.
1. Configure Winlink Express are you would normally. Hopefully you registered!
1. Go ahead and update forms if they've updated.
1. Make the window wide enough to see the session types.
1. Test it with a Telnet Winlink session, as you would normally.
1. Select "VARA FM Winlink" as a session type, and "Open session".
1. Under Settings, select "Show VARA when started" if you like, then Update.
1. Select "Channel Selection" and then "Update Table Via Internet".
1. Choose your radio channel and VARA peer.
1. Make sure your Radio is tuned correctly, your SignaLink is on, and click
"Start".  Winlink Express should use VARA to connect to the RMS.
1. If that worked, you're ready to go!  If not, you may need to tune volume
settings in Linux, or twiddle knobs on the SignaLink.
