### Usage
* Run `RevokeChinaCerts_Online.bat` and follow the messages on screen.
* **Clear all browser(s) data and DNS cache of system**, and restart network interface(s).

### Version
* **Base** is the base version of RevokeChinaCerts, which can revoke some root/intermediate/fake certificates.
* **Extended** is the extended version of RevokeChinaCerts, which can revoke all root/intermediate/fake certificates. **This is the suggestion.**
* **All** is the all version of RevokeChinaCerts, which can revoke all certificates from greater China. **This is the test version.**
* **Restore** is the restore batch, which can restore all revoked certificates.

### Special
* **Some security software will "protect" HTTPS transport with MITM/Man-in-the-middle attack, you must shutdown those modules or uninstall the software!**
* **Extended** and **All** version will revoke `GoAgent CA` using in GoAgent. Please delete `CA.crt` and `certs` folder in GoAgent program folder(if it exists). Finally, clear all browser(s) data and DNS cache of system, restart network interface(s) and restart GoAgent.

### Attention
* Delete certificates cannot revoke them. You must add the certificates to CRL to disable them(or call Revoke).
* You must run the revoking or restoring batches in all users on Windows.
* Most of Windows programs, Chrome and Opera is using system certificate list.

### Usage(without Automation tools)
* **Linux**(Debian, other Linux distributions should need to see its official description)
    * Run `sudo dpkg-reconfigure ca-certificates` in terminal.
    * Using the space bar to revoke the certificates.
    * Using tab and enter key to save changes.
    * Clear all browser(s) data and DNS cache of system, and restart network interface(s).
* **Mac**
    * Open `Utilities` - `Keychain Access` - `Keychains` - `System Roots`
    * Open the certificate and select all `Not trusted`.
    * Clear all browser(s) data and DNS cache of system, and restart network interface(s).
* **Firefox**
    * Open `Tools` - `Options` - `Advanced` - `Certificates` - `View Certificates`
    * Open the certificate and select to disable.
    * Clear all browser(s) data and DNS cache of system, and restart network interface(s).
* **Android**
    * `Setting` - `Security` - `Trusted credentials`
    * Open the certificate and select `Disable`.
    * Clear all browser(s) data and DNS cache of system, and restart network interface(s).
* **iOS**: There are not any ways(Undocumented) to revoke any system root certificates in iOS.

### About Certifications
* Details https://github.com/chengr28/RevokeChinaCerts/tree/master/Shared/Certificates#hunman-readable-certificates-details
* Base list

Name | Organization | SHA-1
----|------|----
CNNIC ROOT | [China Internet Network Information Center](https://www.cnnic.net.cn) | 8BAF4C9B1DF02A92F7DA128EB91BACF498604B6F
China Internet Network Information Center EV Certificates Root | [China Internet Network Information Center](https://evdemo.cnnic.cn) | 4F99AA93FB2BD13726A1994ACE7FF005F2935D1E
GiantRootCA | [ZTGame](https://mail.ztgame.com) | 7514436E903C901069980499CA70DE74FC06C83C
JGZXCA |  | 7A4AA61E2A88704115E47748D8647DAEE6837559
 |  | 
 |  | 
 |  | 
 |  | 
 |  | 
 |  | 
 |  | 



