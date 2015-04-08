### Usage
* Run `RevokeChinaCerts_Control.bat`.
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
See https://github.com/chengr28/RevokeChinaCerts/tree/master/Shared/Certificates#hunman-readable-certificates-details
