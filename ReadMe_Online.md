### Usage
* Run batch **with Administrator permissions** and follow the messages on screen(Windows):
    * `RevokeChinaCerts_Online.bat` - Windows built-in certificate lists
    * `RevokeChinaCerts_Firefox.bat` - Firefox built-in certificate lists
    * Run all batches to revoke certificates in all supported lists.
* See other system folders to revoke certificates in other platforms.
* **Clear all browser(s) data/DNS cache of system** and restart network interface(s).

### Version
* **Base** is the base version of RevokeChinaCerts, which can revoke some root/intermediate/fake certificates.
* **Extended** is the extended version of RevokeChinaCerts, which can revoke all root/intermediate/fake certificates. **This is the suggestion.**
* **All** is the all version of RevokeChinaCerts, which can revoke all certificates from greater China. **This is the test version.**
* **Restore** is the restore batch, which can restore all revoked certificates.

### Special
* **Some security software will "protect" HTTPS transport with MITM/Man-in-the-middle attack, you must shutdown/uninstall these modules/softwares!**
* **Extended** and **All** version will revoke `GoAgent CA` using in GoAgent. Please delete `CA.crt` and `certs` folder in GoAgent program folder(if it exists). Finally, clear all browser(s) data and DNS cache of system, restart network interface(s) and restart GoAgent.

### Attention(Windows)
* Delete certificates cannot revoke them. You must add the certificates to CRL to prohibit all their uses.
* Most of programs, Chrome and Opera are using system certificate list.

### Update(Windows)
* Update **CRL**/Certificate Revocation List
* Update **CTL**/Certificate Trust List(**SST**)
* Update **CTL**/Certificate Trust List(**RootSUPD**)
* To reset all certificate lists, do not choose any options. Exit batch and use Microsoft Fixit tools:
    * **Microsoft_Fixit_20135.diagcab** - Windows Vista and later
    * **Microsoft_Fixit_51014.msi** - Windows XP/2003 and older
* SST database:
    * SST database can be found in [KB2677070/An automatic updater of revoked certificates is available](https://support.microsoft.com/en-us/kb/2677070) and CAB-> STL(Certificate fingerprint list) can be indexed with Certutil tool. Certutil tool can download certificates with STL(`generateSSTFromWU` and `syncWithWU` parameters). About SST database, see [Configure Trusted Roots and Disallowed Certificates](https://TechNet.Microsoft.com/en-us/library/dn265983.aspx).
    * [KB931125/RootSUPD](https://support.Microsoft.com/en-us/KB/931125) with the end of support for Windows XP is no longer be updated.

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

### About Certificates
* See [this link](https://github.com/chengr28/RevokeChinaCerts/tree/master/Shared/Certificates#human-readable-certificates-details) for more details.
* **Base** list

Name | Authority | Fingerprint
:---:|:---:|---
github.com | Fake | 27A29C3A8B3261770E8B59448557DC9E9339E68C
google.com | Fake | F6BEADB9BC02E0A152D71C318739CDECFC1C085D
google.com | Fake | 316076F2866588DBB233C7F9EB68B58125150C21
yahoo.com | Fake | 2290C311EA0F3F57E06DF45B698E18E828E59BC3
hotmai.com | Fake | 30F3B3ADC6E570BDA606B9F96DE24190CE262C67
www.facebook.com | Fake | DC6EE6EDC4C078E1B2C12F6D1985000E27CFD318
www.icloud.com | Fake | F468B5F3FED807974476A22B32EA3137D924F7BA
*.hotmail.com | Fake | 75F411595FE9A21A17A4967C7B666E5152791A32
[CNNIC ROOT](https://www.cnnic.net.cn) | [China Internet Network Information Center](https://www.cnnic.net.cn) | 8BAF4C9B1DF02A92F7DA128EB91BACF498604B6F
[China Internet Network Information Center EV Certificates Root](https://evdemo.cnnic.cn) | [China Internet Network Information Center](https://www.cnnic.net.cn) | 4F99AA93FB2BD13726A1994ACE7FF005F2935D1E
CNNIC SSL | [Entrust.net Secure Server Certification Authority](http://www.entrust.net) | 6856BB1A6C4F76DACA362187CC2CCD484EDDC25D
[GiantRootCA](https://mail.ztgame.com) | [Giant Interactive Group Inc.](http://www.ztgame.com) | 7514436E903C901069980499CA70DE74FC06C83C
[JGZXCA](https://211.146.10.133) | [State Administration of Press, Publication, Radio, Film and Television of The People's Republic of China](http://www.sarft.gov.cn) | 7A4AA61E2A88704115E47748D8647DAEE6837559
Superfish, Inc. | [Superfish, Inc.](http://www.home.superfish.com) | C864484869D41D2B0D32319C5A62F9315AAF2CBD
[*.wacc.baidu.com](https://wacc.n.shifen.com) | [Baidu, inc.](https://www.baidu.com) | 561422647B89BE22F203EBCAEF52B5007227510A
eDellRoot | [Dell Inc.](https://www.dell.com) | 98A04E4163357790C4A79E6D713FF0AF51FE6927

* **Extended** list

Name | Authority | Fingerprint
:---:|:---:|---
[CFCA GT CA](https://cstest.cfca.com.cn) | [China Financial Certification Authority](https://www.cfca.com.cn/) | EABDA240440ABBD694930A01D09764C6C2D77966
CFCA GT CA | [China Financial Certification Authority](https://www.cfca.com.cn/) | A8F2DFE36AE0CC2DB9DD38347D30AED9551DD25A
[CFCA EV ROOT](https://cs.cfca.com.cn) | [China Financial Certification Authority](https://www.cfca.com.cn/) | E2B8294B5584AB6B58C290466CAC3FB8398F8483
[UCA Global Root](https://www.sheca.com) | [Shanghai Electronic Certificate Authority Center Co., Ltd.](https://www.sheca.com) | 0B972C9EA6E7CC58D93B20BF71EC412E7209FABF
[UCA Root](https://ibanks.bankofshanghai.com) | [Shanghai Electronic Certificate Authority Center Co., Ltd.](https://www.sheca.com) | 8250BED5A214433A66377CBC10EF83F669DA3A67
UCA Extended Validation Root | [Shanghai Electronic Certificate Authority Center Co., Ltd.](https://www.sheca.com) | C59DD79CC42245AC7216FDC18524F7D1E4CF1E92
UCA Extended Validation Root | [Shanghai Electronic Certificate Authority Center Co., Ltd.](https://www.sheca.com) | B9C9F58B3BBEF575E2B58328770E7B0076C40B5E
[UCA ROOT](https://ibanks.bankofshanghai.com) | [Shanghai Electronic Certificate Authority Center Co., Ltd.](https://www.sheca.com) | 3120F295417730075F8CD42D0CAE008EB5726EF8
GoAgent CA | [GoAgent project](https://github.com/GoAgent/GoAgent) | AB702CDF18EBE8B438C52869CD4A5DEF48B40E33
GDCA TrustAUTH R2 ROOT | [GUANG DONG CERTIFICATE AUTHORITY](http://www.gdca.com.cn) | ‎742CA08594ABA62CE76E94386EA75A98712F02EA
GDCA TrustAUTH R5 ROOT | [GUANG DONG CERTIFICATE AUTHORITY](http://www.gdca.com.cn) | 0F36385B811A25C39B314E83CAE9346670CC74B4

* **All** list

Name | Authority | SHA-1
:---:|:---:|---
[SRCA](https://kyfw.12306.cn) | [Sinorail Certification Authority](http://www.12306.cn) | AE3F2E66D48FC6BD1DF131E89D768D505DF14302
[CERNET CA](https://www.nic.edu.cn) | [The China Education and Research Network](http://www.cernet.edu.cn) | ‎8EF134D4BAD5498E348A7C6D9B66F67A09D56D9B
[Certification Authority of WoSign](https://root1evtest.wosign.com) | [WoSign CA Limited](https://www.wosign.com) | B94294BF91EA8FB64BE61097C7FB001359B676CB
[CA 沃通根证书](https://root2evtest.wosign.com) | [WoSign CA Limited](https://www.wosign.com) | 1632478D89F9213A92008563F5A4A7D312408AD6
Class 1 Primary CA | [WoSign CA Limited](https://www.wosign.com) | 6A174570A916FBE84453EED3D070A1D8DA442829
Certification Authority of WoSign | [WoSign CA Limited](https://www.wosign.com) | 33A4D8BC38608EF52EF0E28A35091E9250907FB9
[Certification Authority of WoSign G2](https://root4evtest.wosign.com) | [WoSign CA Limited](https://www.wosign.com) | FBEDDC9065B7272037BC550C9C56DEBBF27894E1
[CA WoSign ECC Root](https://root5evtest.wosign.com) | [WoSign CA Limited](https://www.wosign.com) | D27AD2BEED94C0A13CC72521EA5D71BE8119F32B
Certification Authority of WoSign | [StartCom Certification Authority](https://www.startcom.org) | 868241C8B85AF79E2DAC79EDADB723E82A36AFC3
Certification Authority of WoSign | [StartCom Certification Authority](https://www.startcom.org) | 692790DA5189529CC5CE1E16E984277A03023E99
Certification Authority of WoSign | [StartCom Certification Authority](https://www.startcom.org) | 804E5FB7DE84F5F5B28347233EAF07846B6070D3
Certification Authority of WoSign | [StartCom Certification Authority](https://www.startcom.org) | B0B68AE97CFE2AFACD0DC2010B9D70ACE593E8A6
CA 沃通根证书 | [StartCom Certification Authority](https://www.startcom.org) | D8EFF6C28BB508E4702565F42748454A872BD412
CA 沃通根证书 | [StartCom Certification Authority](https://www.startcom.org) | CE335662F0EA6764B95C7F50A995A514ACE8C815
Certification Authority of WoSign | [UTN – DATACorp SGC](https://www.comodo.com) | 56FAADDC596DCF78D585D83A35BC04B690D12736
WoSign Premium Server Authority | [AddTrust External CA Root/UTN-USERFirst-Hardware](https://www.comodo.com) | E3D569137E603E7BACB6BCC66AE943850C8ADF38
WoSign Server Authority | [AddTrust External CA Root/UTN-USERFirst-Hardware](https://www.comodo.com) | 3E14B8BD6C568657D852D95D387249AE857B4A39
WoSign SGC Server Authority | [UTN – DATACorp SGC](https://www.comodo.com) | 6D5A18050D56BFDE525CBE89E8C45DD1B53D12E9
WoSign Client Authority | [UTN-USERFirst-Client Authentication and Email](https://www.comodo.com) | FAD4319D4E173FF3853E51C98D21919BF3DA1A1E
WoTrust Premium Server Authority | [AddTrust External CA Root/UTN-USERFirst-Hardware](https://www.comodo.com) | 381CBC5048AFD9A02D3E5882D5F22D962B1A5F72
WoTrust Server Authority | [AddTrust External CA Root/UTN-USERFirst-Hardware](https://www.comodo.com) | 337DF96418F08A9355870513AFCEBDC68BCED767
WoTrust SGC Server Authority | [UTN – DATACorp SGC](https://www.comodo.com) | 46A762F3C3CF3732DE22A8BA1EBBA3BC048F9B8C
WoTrust Client Authority | [UTN-USERFirst-Client Authentication and Email](https://www.comodo.com) | 38CFE78D9F1F0B0637AFCAAA3D5549D87C0AA1D0
Hongkong Post Root CA | [Hongkong Post](https://www.hongkongpost.hk) | E0925E18C7765E22DABD9427529DA6AF4E066428
[Hongkong Post Root CA 1](https://www.hongkongpost.hk) | [Hongkong Post](https://www.hongkongpost.hk) | D6DAA8208D09D2154D24B52FCB346EB258B28A58
Macao Post eSignTrust Root Certification Authority | [Macao Post eSignTrust Certification Services](https://www.esigntrust.com) | 89C32E6B524E4D65388B9ECEDC637134ED4193A3
Macao Post eSignTrust Root Certification Authority(G02) | [Macao Post eSignTrust Certification Services](https://www.esigntrust.com) | 06143151E02B45DDBADD5D8E56530DAAE328CF90
[ePKI Root Certification Authority](https://epki.com.tw) | [Chunghwa Telecom ecommerce Public Key Infrastructure](https://epki.com.tw) | 67650DF17E8E7E5B8240A4F4564BCFE23D69C6F0
Government Root Certification Authority | [Government Root Certification Authority](http://grca.nat.gov.tw/GRCAeng/htdocs/index.html) | F48B11BFDEABBE94542071E641DE6BBE882B40B9
TWCA Global Root CA | [TWCA](https://www.twca.com.tw) | 9CBB4853F6A4F6D352A4E83252556013F5ADAF65
[TWCA Root Certification Authority(1)](https://www.twca.com.tw) | [TWCA](https://www.twca.com.tw) | CF9E876DD3EBFC422697A3B5A37AA076A9062348
TWCA Root Certification Authority(2) | [TWCA](https://www.twca.com.tw) | DF646DCB7B0FD3A96AEE88C64E2D676711FF9D5F
TaiCA Secure CA | [GTE CyberTrust Global Root](http://www.verizonenterprise.com) | 5B404B6DB43E1F71557F75552E7668289B1B6309
TWCA Secure CA | [Baltimore CyberTrust Root](http://www.verizonenterprise.com) | 3F3E6C4B33802A2FEA46C5CACA14770A40018899
TWCA Secure Certification Authority | [AddTrust External CA Root](https://www.comodo.com) | 339D811FEC673E7F731307A34C7C7523ABBE7DFE
TWCA Secure Certification Authority | [AddTrust External CA Root](https://www.comodo.com) | 339D811FEC673E7F731307A34C7C7523ABBE7DFE