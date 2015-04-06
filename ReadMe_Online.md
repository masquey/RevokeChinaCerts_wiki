### Usage
* Run(as Common user **and** as Administrator, need twice) `RevokeChinaCerts_Online.bat`.
* Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Experimental, but strongly recommended)

### Version
* **Base** is the base version of RevokeChinaCerts, which can revoke some root/intermediate/fake certificates.
* **Extended** is the extended version of RevokeChinaCerts, which can revoke all root/intermediate/fake certificates. **This is the suggestion.**
* **All** is the all version of RevokeChinaCerts, which can revoke all certificates from greater China. **This is the test version.**
* **Restore** is the restore batch, which can restore all revoked certificates.
* The list of certificates is in About Certificates section.

### Special
* **Some security software will "protect" HTTPS transport with MITM/Man-in-the-middle attack, you must shutdown those modules or uninstall the software!**
* **Extended** and **All** version will revoke `GoAgent CA` using in GoAgent. Please delete `CA.crt` and `certs` folder in GoAgent program folder(if it exists). Finally, clear all browser(s) data and restart GoAgent.

### Attention
* Windows
    * Delete certificate cannot revoke it. You must add the certificate to CRL to disable it(or call Revoke).
    * You must run the revoking or restoring batch in all users in Windows.
    * Most of Windows programs, Chrome and Opera is using system certificate list.
* Firefox
    * `CNNIC ROOT` and `China Internet Network Information Center EV Certificates Root` in Firefox 32.
* iOS
    * There are not any ways(Undocumented) to revoke any system root certificates in iOS.

### Usage(without Automation tools)
* Linux(Debian, other Linux distributions should need to see its official description.)
    * Run `sudo dpkg-reconfigure ca-certificates` in terminal.
    * Using the space bar to revoke the certificates.
    * Using tab and enter key to save changes.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Experimental, but strongly recommended)
* Mac
    * Open `Utilities` - `Keychain Access` - `Keychains` - `System Roots`
    * Open the certificate and select all `Not trusted`.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Experimental, but strongly recommended)
* Firefox
    * Open `Tools` - `Options` - `Advanced` - `Certificates` - `View Certificates`
    * Open the certificate and select to disable.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Experimental, but strongly recommended)
* Android
    * `Setting` - `Security` - `Trusted credentials`
    * Open the certificate and select `Disable`.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Experimental, but strongly recommended)

### About Certifications
See https://github.com/chengr28/RevokeChinaCerts/tree/master/Shared/Certificates#hunman-readable-certificates-details