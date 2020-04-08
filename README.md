# Windows_Server_Optimization
PowerShell Windows Server Optimization Tool
3. How to work – PowerShell script parameters.

The Script allows the following functionalities:

-	NIC configuration, is posible configure a IP address, DNS and GATEWAY.
o	The Script ask if your desire configure a network interface card, press “y” for yes.
        Add the IP Address
        Add the Subnet Mask
        Add the default Gateway
        Add the DNS Servers
          •	The DNS configuration is posible using a delimeters “” and IPaddress Example :
            o	Example A :  “192.168.1.90”, “192.168.1.91”
            o	Example B :   “192.169.1.90”
        The domain is a domain suffix.

If your not answer with “y” the script execute the next option.

-	NIC configuration, Network Interface Card, this configuration is applied to advanced configuration WINS tab :
-	The parameters to your especified to execute this module:

  Netbios (0-enable 1-NB over TCP, 2 TCP)::_

          o	Use 0 for Netbios/DHCP (for a DHCP , if your not use a static IP Address)
          o	Use 1 para Netbios over TCP (if your use a static IP Address and NetBios)
          o	Use 2 para TCP (if your use a static IP Address without Netbios, native option)

 
Var definition values
----------------------
TEMP and TMP parameters
Determines the TEMP and TMP folders, normally the best practice is use a centralized shared folder, this centralized shared folder normally is located to a Storage same to SAN.

The %username% specified to a user, uses a other location, for example: 

\\<Storage_Folder>\%USERNAME%\Temporal\TMP 
\\<Storage_Folder>\%USERNAME%\Temporal\TEMP

The variables used for change this configuration is a $temp_path and $tmp_path : 

$temp_path = "%USERPROFILE%\AppData\Local\Temp"
$tmp_path = "%USERPROFILE%\AppData\Local\Tmp" 

Menu Show Delay parameter
Determines the interval from the time the cursor is pointed at a menu until the menu items are displayed. The default value is 400, is this case is applied one value to 100. The variable used is $menu_delay

$menu_delay = 100 

Encoding User Preferences Mask parameter
Determines the configuration por a Desktop optimization, if one user not use a RemoteApp and access to Windows Server Desktop, this changes applied directly to registry Key: HKEY_USERS\.DEFAULT\Control Panel\Desktop

$string_desktop =  0x90,0x12,0x01,0x80,0x10,0x00,0x00,0x00 

The values is applied using this Microsoft documentation: https://technet.microsoft.com/en-us/library/cc957204.aspx
 

How to Start the Script

Save the script code included in this document to a .ps1 file, and copy to a specified server folder, for example: C:\TESTSCRIPT , 
for execution process your start since Powershell (CMD) command line (example) : 

PS C:\Users\Administrator.TEST> .\SRV_Optimizationv3.3_Tool.ps1

The Script is started and display all process to execute and what modifications is applied to the local server.
 
Features for this release.
--------------------------
-	Network Interface Card configuration
-	PageFile is changed in this Server caculated automatically depends to Server Memory.
-	ClearPageFile Shutdown
-	UAC is Disabled
-	Crash Dump Configuration is Disabled [Disabled: Event Log, Auto Reboot and Crash Dump File]
-	Hibernate is Disabled
-	Paging Executive is Disable
-	Disable Task Offload
-	AutoLayout is Enabled
-	Hand Error Messages is Disabled
-	Services Timeout Increased
-	Max Token Size Modified
-	ActiveDesktop & CIFS Disabled
-	NFS Disable Last Access Time Stamp is Applied
-	Only Enable Print Error Event is Applied
-	Google Schedule Task is Disabled
-	Adobe Flash Player Updater Schedule Task is Disabled
-	TEMP and TMP Configuration [Standard: %USERPROFILE%\AppData\Local\Temp]
      o	TEMP parameter 
      o	TMP parameter 
-	Menu is accelerated
-	Windows Error Reporting is Disabled
-	Drag Full Windows is Disabled
-	Font Smoothing is Disabled
-	User Preferences Mask Modified
-	Minimum Animated Windows Metrics Modified
-	Don't check Windows Update is applied - Disable AutoUpdate
-	For a RDSH Server.
    o	Delete temporal folders on exit. – Enabled.
    o	Use a temporaly folder per session. – Enabled.
