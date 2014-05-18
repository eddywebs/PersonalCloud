## Personal Cloud

Personal cloud is a Raspberry Pi OS image based on raspbian (debian wheezy), it comes with dropbox clone (ownCloud), a download manager (aria2) and MiniDLNA /UPnP media server.

Flash the image, connect an external to your raspberry pi and have full media server, a download box and web file manager ready with minimal configuration.

## Motivation

Dropbox requires a subscription fee for any larger(>5gigs) storage limit, initiating a file download away from home computer can be challenging. 
Having a dedicated media server apears to be an expensive or techincal propostion for many.

All the above achieved with<$50 (excludes external storage cost).
No subscription fee ! minimal techincal skills required.


## Installation

 * Download the image from : http://eddywebs.com/personalCloud.zip

 * Flash to SD card (min 8GB capacity required)

 * Power up the raspberryPi and connect it a network.
  * It is advised to use Ethernet connection for faster performance
  * In case wireless dongle is used: wifi network can be defined at /etc/wpa_supplicant/wpa_supplicant.conf which autoconnects at boot.


 * Mount the external drive. You may use guide at  >> http://www.techjawab.com/2013/06/how-to-setup-mount-auto-mount-usb-hard.html

  * Make sure to mount the external hard dive to /media/hdd1 mount point under the user: www-data, group: www-data. This is because all the applications are set to read the data from directory /media/hdd1. 
  This maybe changed/added by adjusting package configurations accordingly.

#Usage and Logins

Find the local ip address of the raspberry pi, 

 * Login to raspbian ssh using ssh pi@youRaspberryPiHost
    * user: pi, password: pi
    
 * Owncloud(dropbox clone) http://youRaspberryPiHost/owncloud
    * owncloud admin user: admin, password: pi
    * Data Dir: /media/hdd1 (mount the hdd/usb on this folder)

 * Aria2 (web download manager) http://youRaspberryPiHost/webui-Aria2
 * Samba/network share /raspberrypi/personalCloud user pi, password: pi

 * MiniDlna/UPnP shows up as personalCloud in all MiniDlna devices and reads all the media directory present in /media/hdd1 directory.

#Furether Configuration
 * Remote Access using PageKite (signup at pagekite.org)- a reversy proxe application to access systems outside localnetwork.
    * Edit script at /startPageKite and switch the KITENAME variable to kite created at pagekite.net, execute the script and you should be able to access the applications at whateverPageKiteName.pagekite.me/owncloud ..... 
 * Push notifications on download-complete using aria2 (signup and download app at pushbullet.com) 
 * edit /notifyPushBullet script with your info at pushbullet.com  
 
## Contributors

Alec Resnick (https://github.com/aresnick) - Figuring out networking.
