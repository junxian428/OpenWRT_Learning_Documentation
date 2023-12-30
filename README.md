# OpenWRT_Learning_Documentation

Download OpenWRT x86 Image Download
Extract the OpenWRT image
Convert OpenWRT Image to VDI

cd %programfiles%/Oracle/Virtualbox
vboxmanage.exe convertdd "%userprofile%\downloads\openwrt-19.07.6-x86-64-combined-ext4.img" "%userprofile%\downloads\openwrt.vdi"

Resize the VDI File

vboxmanage.exe modifyhd --resize 512 "%userprofile%\downloads\openwrt.vdi"

Create new VM

Name: OpenWRT
Machine Folder: C:\VMs
Type: Linux
Version: 2.6 / 3.x / 4.x (64-bit)
Memory Size: 128 MB
Hard disk: Do not add a virtual hard disk

![image](https://github.com/junxian428/OpenWRT_Learning_Documentation/assets/58724748/12c129c9-c321-433c-b8ae-eb79251f8ce6)

Click Create
Move the openwrt.vdi file from downloads into C:\VMs\OpenWRT
Select the VM and Click Settings
Select Storage
Click Add Storage Attachment > Add Hard Disk > Choose existing disk
Click Add and browse to C:\VMs\OpenWRT\openwrt.vdi
Click OK
Select Network
Set Adapter 1 Attached to: Bridged
Click the Adapter 2 tab
Check the Enable Network Adapter box
Set Adapter 2 Attached to: Bridged
Click OK
Make sure the OpenWRT VM is selected and click Start > Normal
Wait for the text to stop scrolling and press Enter
Run the following command to change/set the root password


passwd


Type a new root password twice to set it
Continue the configuration by running the following commands
# set the lan ip address
uci set network.lan.ipaddr='192.168.0.251'
# restart network services
service network restart
# update openwrt packages
opkg update
# install the luci web ui
opkg install luci
Open a web browser and navigate to http://IPofVM, http://192.168.0.251 in the example
At the login screen, enter the username root and the password set above > Click the Login button
Enjoy OpenWRT running in VirtualBox
