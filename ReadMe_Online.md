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
* See [this Link](https://github.com/chengr28/RevokeChinaCerts/tree/master/Shared/Certificates#hunman-readable-certificates-details) for details.
* **Base** list

Name | Authority| Date | SHA-1
---|---|---|---
github.com | Fake | 2013-01-25 | 27A29C3A8B3261770E8B59448557DC9E9339E68C
google.com | Fake | 2014-09-01 | F6BEADB9BC02E0A152D71C318739CDECFC1C085D
google.com | Fake | 2014-10 | 316076F2866588DBB233C7F9EB68B58125150C21
yahoo.com | Fake | 2014-09-30 | 2290C311EA0F3F57E06DF45B698E18E828E59BC3
hotmai.com | Fake | 2014-10-02 | 30F3B3ADC6E570BDA606B9F96DE24190CE262C67
www.facebook.com | Fake | 2014-10-08 | DC6EE6EDC4C078E1B2C12F6D1985000E27CFD318
www.icloud.com | Fake | 2014-10-18 | F468B5F3FED807974476A22B32EA3137D924F7BA
*.hotmail.com | Fake | 2015-01-17 | 75F411595FE9A21A17A4967C7B666E5152791A32
[CNNIC ROOT](https://www.cnnic.net.cn) | [China Internet Network Information Center](https://www.cnnic.net.cn) | - | 8BAF4C9B1DF02A92F7DA128EB91BACF498604B6F
[China Internet Network Information Center EV Certificates Root](https://evdemo.cnnic.cn) | [China Internet Network Information Center](https://www.cnnic.net.cn) | - | 4F99AA93FB2BD13726A1994ACE7FF005F2935D1E
CNNIC SSL | [Entrust.net Secure Server Certification Authority](http://www.entrust.net) | - | 6856BB1A6C4F76DACA362187CC2CCD484EDDC25D
[GiantRootCA](https://mail.ztgame.com) | [Giant Interactive Group Inc.](http://www.ztgame.com) | - | 7514436E903C901069980499CA70DE74FC06C83C
[JGZXCA](https://211.146.10.133) | [State Administration of Press, Publication, Radio, Film and Television of The People's Republic of China](http://www.sarft.gov.cn) | - | - | 7A4AA61E2A88704115E47748D8647DAEE6837559
Superfish, Inc. | [Superfish, Inc.](http://www.home.superfish.com) | - | C864484869D41D2B0D32319C5A62F9315AAF2CBD
[*.wacc.baidu.com](https://wacc.n.shifen.com) | [Baidu, inc.](https://www.baidu.com) | - | 561422647B89BE22F203EBCAEF52B5007227510A
