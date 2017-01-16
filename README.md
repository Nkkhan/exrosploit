# exrosploit
Classification-Banner
=====================

Classification Banner is a python script that will display the
classification level banner of a session with a variety of
configuration options on the primary screen.  This script can
help government and possibly private customers display a 
notification that sensitive material is being displayed - for 
example PII or SECRET Material being processed in a graphical
session. The script has been tested on a variety of graphical
environments such as GNOME2, GNOME3, KDE, twm, icewm, and Cinnamon.

Python script verified working on RHEL 5/6/7 and Fedora 12-25.

Selecting the classification window and pressing the ESC key
will temporarily hide the window for 15 seconds, it will return
to view after that


Classification Banner Usage
===========================

Options should be placed in the '/etc/classification-banner' file.

 message      - The classification level to display (Default: 'UNCLASSIFIED')
 fgcolor      - Foreground color of the text to display (Default: '#00CC00' "Green")
 bgcolor      - Background color of the banner the text is against (Default: '#000000' "Black")
 face         - Font face to use for the displayed text (Default: 'liberation-sans')
 size         - Size of font to use for text (Default: 'small')
 weight       - Bold or normal (Default: 'bold')
 show_top     - Show top banner (Default: True)
 show_bottom  - Show bottom banner (Default: True)
 hres         - Manually Set Horiztonal Resolution (OPTIONAL) [ if hres is set, vres required ]
 vres         - Manually Set Horiztonal Resolution (OPTIONAL) [ if vres is set, hres required ]
 opacity      - Sets opacity - for composted window managers only (OPTIONAL) [float - range 0 .. 1] (Default 0.75)
 
Command line options that correspond to the above settings:

 -m, --message
 -f, --fgcolor
 -b, --bgcolor
 --face
 --size
 --weight
 --hide-top
 --hide-bottom
 -x, --hres
 -y, --vres
 -o, --opacity

Examples
========

These are examples for the configuration of the Classification Banner
using the '/etc/classification-banner' file for various classifications
based upon generally accepted color guidelines in the DoD/IC.

    Default (UNCLASSIFIED)
        
    CONFIDENTIAL
    
        message='CONFIDENTIAL'
        bgcolor='#33FFFF'
    
    SECRET
        
        message='SECRET'
        fgcolor='#FFFFFF'
        bgcolor='#FF0000'
    
    TOP SECRET
        
        message='TOP SECRET'
        fgcolor='#FFFFFF'
        bgcolor='#FF9900'
        
    TOP SECRET//SCI
        
        message='TOP SECRET//SCI'
        bgcolor='#FFFF00'


Autostart
=========

To auto-start the classification-banner script on the GNOME Desktop, 
create the following file:

# vi /etc/xdg/autostart/classification-banner.desktop

     [Desktop Entry]
     Name=Classification Banner
     Exec=/usr/local/bin/classification-banner.py
     Comment=User Notification for Security Level of System.
     Type=Application
     Encoding=UTF-8
     Version=1.0
     MimeType=application/python;
     Categories=Utility;
     X-GNOME-Autostart-enabled=true
     StartupNotify=false
     Terminal=false
