Troubleshooting
-
```
/overlay/usr/bin/vpnserver: can't resolve symbol 'SHA' in lib '/overlay/usr/bin/vpnserver'.
```
You need install the libopenssl compiled for the SoftEther VPN.

```
-- Alert: SoftEther VPN Kernel --
String Library Init Failed.
Please check your locale settings and iconv() libraries.
```
This error occurs when not set the LANG environment variable.
You need set the LANG environment variable and execute the SoftEther VPN.

e.g.
```
env LANG=en_US.UTF-8 /overlay/usr/bin/vpnserver start
```

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

e.g.
```
opkg install --force-overwrite http://b.mikomoe.jp/download/1412375380/attach/softethervpnserver_4.10-9505_ar71xx.ipk
```
