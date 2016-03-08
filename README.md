Troubleshooting
-

####aaaa
```
/overlay/usr/bin/vpnserver: can't resolve symbol 'SHA' in lib '/overlay/usr/bin/vpnserver'.
```
You need install the libopenssl compiled for the SoftEther VPN.

####aaaa
```
-- Alert: SoftEther VPN Kernel --
String Library Init Failed.
Please check your locale settings and iconv() libraries.
```
This error occurs when not set the LANG environment variable.  
You need set the LANG environment variable and execute the SoftEther VPN.

e.g.:
```
env LANG=en_US.UTF-8 /overlay/usr/bin/vpnserver start
```

####aaaa
```
Installing softethervpncmd (4.10-9505) to root...
Collected errors:
 * check_data_file_clashes: Package softethervpncmd wants to install file /usr/bin/hamcore.se2
        But that file is already provided by package  * softethervpnclient
```
Each SoftEther VPN package included hamcore.se2.  
This means collision when install other SoftEther VPN packages.  
Install package from the LuCI or execute the opkg command with "--force-overwrite" option.  
This will you can install successfully.

e.g.:
```
opkg install --force-overwrite http://b.mikomoe.jp/download/1412375380/attach/softethervpnserver_4.10-9505_ar71xx.ipk
```

*force*
**force**

SoftEther VPN for OpenWrt
=
Your router is if ar71xx or brcm47xx, You do not need build steps.  
You can get binary package from http://b.mikomoe.jp/.

If need compile for OpenWrt 12.09, See old [README.MD](https://github.com/el1n/OpenWRT-package-softether/blob/7dc4c4ce19da9aa7dc2330e2dbbdc4d3e4dd4fcc/README.md).  

See [Alberts00](https://github.com/Alberts00)'s blog if you want more detailed guide.  
Also you can download SE4WRT Chaos Calmer(15.05) build from his website.

If you are japanese or could read japanese, Visit [my blog](http://elin.mikomoe.jp/index.php?entry=OpenWRT%E3%81%A7SoftEther-VPN%E3%82%92%E5%8B%95%E3%81%8B%E3%81%99).  
Since this entry too old, i recommend read this README.MD if possible.

Note
-
+ No more need customized libopenssl for Jan 15, 2015 or later version.

+ Every SoftEther VPN packages did integrated for Feb 10, 2015 or later version.
Binary has function of vpnserver/vpnclient/vpnbridge/vpncmd like busybox now.
Uninstall all the SoftEther VPN packages if you will update from old version.

Compile and Install
-
1. Install the packages required to compile

  Example for debian.
  ```
  apt-get install -y subversion make gcc g++ libncurses5-dev libghc-zlib-dev libreadline-dev libssl-dev gawk bzip2 patch xz-utils sudo
  ```


6. Execute

  Press "Start" from "System -> Startup" in the LuCI.

  If you want run SoftEther VPN in a shell, You need set the LANG environment variable and execute the SoftEther VPN.
  ```
  /usr/bin/env LANG=en_US.UTF-8 /usr/bin/vpnserver start
  ```

Thanks
-
+ [Alberts00](https://github.com/Alberts00)
