### Batch version(Windows)
* **Base** is the base version of RevokeChinaCerts, which can revoke some root/intermediate/fake certificates.
* **Extended** is the extended version of RevokeChinaCerts, which can revoke all root/intermediate/fake certificates. **This is the suggestion.**
* **All** is the all version of RevokeChinaCerts, which can revoke all certificates from greater China. **This is the test version.**
* **Restore** is the restore batch, which can restore all revoked certificates.
* The list of certificates is in About Certificates section.

### Special
* **Extended** and **All** version will revoke `GoAgent CA` using in GoAgent. Please delete `CA.crt` and `certs` folder in GoAgent program folder(if it exists). Finally, clear all browser(s) data and restart GoAgent.

### Usage
* Windows
    * Choose the version and run `.bat` file.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Optional, but strongly recommended)
* Linux(Debian, other Linux distributions should need to see its official description.)
    * Execute `sudo dpkg-reconfigure ca-certificates` in terminal.
    * Using the space bar to revoke the certificates.
    * Using tab and enter key to save changes.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Optional, but strongly recommended)
* Mac
    * Using shell script
        * Get the root permission with `sudo` and run `RevokeChinaCerts.sh`.
    * Manually
        * Open `Utilities` - `Keychain Access` - `Keychains` - `System Roots`
        * Open the certificate and select all `Not trusted`.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Optional, but strongly recommended)
* Firefox
    * Open `Tools` - `Options` - `Advanced` - `Certificates` - `View Certificates`
    * Open the certificate and select to disable.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Optional, but strongly recommended)
* Android
    * `Setting` - `Security` - `Trusted credentials`
    * Open the certificate and select `Disable`.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Optional, but strongly recommended)

### Explanation
* Windows
    * Delete certificate can not revoke it. You must add the certificate to CRL to disable it(or call Revoke).
    * Most of Windows programs, Chrome and Opera is using system certificate list.
* Linux
    * Different Linux distributions need different process, see its official description.
* Mac
    * `CNNIC ROOT`, `China Internet Network Information Center EV Certificates Root`, `UCA Global Root` and `UCA Root` in OS X Yosemite and old versions.
* Firefox
    * `CNNIC ROOT` and `China Internet Network Information Center EV Certificates Root` in Firefox 32.
* Android
    * `CNNIC ROOT` and `China Internet Network Information Center EV Certificates Root` in Android 5.0.1 and old versions.

### Attention
* Windows
    * You must run the revoking or restoring batch in all users in Windows.
* Android
    * Pay attention to any certificate errors, it can be ignored in Android.
    * Android not trust certificates which are not in list of system.
* iOS
    * There are not any ways(Undocumented) to revoke any system root certificates in iOS.

### About Certifications
* **Base version**
    * **Man-In-The-Middle attacking fake certificates**
    * Fake GitHub.Com(2013-01-25)
        * SHA-1 is `27A29C3A8B3261770E8B59448557DC9E9339E68C`
        * MITM GitHub in 2013-01-25.
    * Fake Google.Com(2014-07-24)
        * SHA-1 is `F6BEADB9BC02E0A152D71C318739CDECFC1C085D`
        * MITM  Google in 2014-09-01.
    * Fake Google.Com(2014-09-18)
        * SHA-1 is `316076F2866588DBB233C7F9EB68B58125150C21`
        * MITM Google when using IPv6 tunneling in October, 2014.
    * Fake Yahoo.Com(2014-09-23)
        * SHA-1 is `2290C311EA0F3F57E06DF45B698E18E828E59BC3`
        * MITM Yahoo in 2014-09-30.
    * Fake Hotmai.Com(2014-10-02)
        * SHA-1 is `30F3B3ADC6E570BDA606B9F96DE24190CE262C67`
        * MITM Microsoft in 2014-10-02.
    * Fake Www.Facebook.Com(2014-10-08)
        * SHA-1 is `DC6EE6EDC4C078E1B2C12F6D1985000E27CFD318`
        * MITM Facebook when using CERNET IPv6 or IPv6 tunneling in 2014-10-08.
    * Fake Www.Icloud.Com(2014-10-04)
        * SHA-1 is `F468B5F3FED807974476A22B32EA3137D924F7BA`
        * MITM Apple iCloud in 2014-10-18.
    * **[China Internet Network Information Center/CNNIC/中国互联网络信息中心](http://www.cnnic.net.cn)**
    * CNNIC ROOT
        * SHA-1 is `8BAF4C9B1DF02A92F7DA128EB91BACF498604B6F`
        * [Test site](https://www.cnnic.net.cn)
    * China Internet Network Information Center EV Certificates Root
        * SHA-1 is `4F99AA93FB2BD13726A1994ACE7FF005F2935D1E`
        * [Test site](https://evdemo.cnnic.cn)
    * CNNIC SSL
        * SHA-1 is `6856BB1A6C4F76DACA362187CC2CCD484EDDC25D`
        * Intermediate certificate of Entrust.net Secure Server Certification Authority
    * **[Baidu/百度公司](http://www.baidu.com)**
    * Baidu WACC service
        * SHA-1 is `561422647B89BE22F203EBCAEF52B5007227510A`
        * [Test site](https://wacc.n.shifen.com)
    * **[Giant Interactive Group Inc./巨人网络](http://www.ztgame.com)**
    * GiantRootCA
        * SHA-1 is `7514436E903C901069980499CA70DE74FC06C83C`
        * [Test site](https://mail.ztgame.com)
* **Extended version**
    * **[China Financial Certification Authority/CFCA/中国金融认证中心](http://www.cfca.com.cn)**
    * CFCA GT CA
        * SHA-1 is `EABDA240440ABBD694930A01D09764C6C2D77966`
        * [Test site](https://cstest.cfca.com.cn)
    * CFCA GT CA
        * SHA-1 is `A8F2DFE36AE0CC2DB9DD38347D30AED9551DD25A`
    * CFCA EV ROOT
        * SHA-1 is `E2B8294B5584AB6B58C290466CAC3FB8398F8483`
        * [Test site](https://cs.cfca.com.cn)
    * UCA Global Root
        * SHA-1 is `0B972C9EA6E7CC58D93B20BF71EC412E7209FABF`
        * [Test site](https://www.sheca.com)
    * UCA Root
        * SHA-1 is `8250BED5A214433A66377CBC10EF83F669DA3A67`
        * [Test site](https://ibanks.bankofshanghai.com)
    * UCA Extended Validation Root
        * SHA-1 is `B9C9F58B3BBEF575E2B58328770E7B0076C40B5E`
    * UCA ROOT
        * SHA-1 is `3120F295417730075F8CD42D0CAE008EB5726EF8`
        * [Test site](https://ibanks.bankofshanghai.com)
    * **Default certificate of [GoAgent](https://github.com/goagent/goagent)**
    * GoAgent CA
        * SHA-1 is `AB702CDF18EBE8B438C52869CD4A5DEF48B40E33`
* **All version**
    * **[Sinorail Certification Authority/SRCA/中铁数字证书认证中心](http://www.12306.cn)**
    * SRCA
        * SHA-1 is `AE3F2E66D48FC6BD1DF131E89D768D505DF14302`
        * [Test site](https://kyfw.12306.cn)
    * **[沃通CA](http://www.wosign.com)**
    * Certification Authority of WoSign
        * SHA-1 is `B94294BF91EA8FB64BE61097C7FB001359B676CB`
        * [Test site](https://www.wosign.com)
    * CA 沃通根证书
        * SHA-1 is `1632478D89F9213A92008563F5A4A7D312408AD6`
    * Class 1 Primary CA
        * SHA-1 is `6A174570A916FBE84453EED3D070A1D8DA442829`
    * Certification Authority of WoSign
        * SHA-1 is `33A4D8BC38608EF52EF0E28A35091E9250907FB9`
    * Certification Authority of WoSign
        * SHA-1 is `868241C8B85AF79E2DAC79EDADB723E82A36AFC3`
        * Intermediate certificate of StartCom Certification Authority
    * Certification Authority of WoSign
        * SHA-1 is `868241C8B85AF79E2DAC79EDADB723E82A36AFC3`
        * Intermediate certificate of StartCom Certification Authority
    * Certification Authority of WoSign
        * SHA-1 is `692790DA5189529CC5CE1E16E984277A03023E99`
        * Intermediate certificate of StartCom Certification Authority
    * Certification Authority of WoSign
        * SHA-1 is `804E5FB7DE84F5F5B28347233EAF07846B6070D3`
        * Intermediate certificate of StartCom Certification Authority
    * CA 沃通根证书
        * SHA-1 is `D8EFF6C28BB508E4702565F42748454A872BD412`
        * Intermediate certificate of StartCom Certification Authority
    * Certification Authority of WoSign
        * SHA-1 is `56FAADDC596DCF78D585D83A35BC04B690D12736`
        * Intermediate certificate of UTN - DATACorp SGC
    * WoSign Premium Server Authority
        * SHA-1 is `E3D569137E603E7BACB6BCC66AE943850C8ADF38`
        * Intermediate certificate of AddTrust External CA Root/UTN-USERFirst-Hardware
    * WoSign Server Authority
        * SHA-1 is `3E14B8BD6C568657D852D95D387249AE857B4A39`
        * Intermediate certificate of AddTrust External CA Root/UTN-USERFirst-Hardware
    * WoSign SGC Server Authority
        * SHA-1 is `6D5A18050D56BFDE525CBE89E8C45DD1B53D12E9`
        * Intermediate certificate of UTN - DATACorp SGC
    * WoSign Client Authority
        * SHA-1 is `FAD4319D4E173FF3853E51C98D21919BF3DA1A1E
        * Intermediate certificate of UTN-USERFirst-Client Authentication and Email
    * WoTrust Premium Server Authority
        * SHA-1 is `381CBC5048AFD9A02D3E5882D5F22D962B1A5F72`
        * Intermediate certificate of AddTrust External CA Root/UTN-USERFirst-Hardware
    * WoTrust Server Authority
        * SHA-1 is `337DF96418F08A9355870513AFCEBDC68BCED767`
        * Intermediate certificate of AddTrust External CA Root/UTN-USERFirst-Hardware
    * WoTrust SGC Server Authority
        * SHA-1 is `46A762F3C3CF3732DE22A8BA1EBBA3BC048F9B8C`
        * Intermediate certificate of UTN - DATACorp SGC
    * WoTrust Client Authority
        * SHA-1 is `38CFE78D9F1F0B0637AFCAAA3D5549D87C0AA1D0`
        * Intermediate certificate of UTN-USERFirst-Client Authentication and Email
    * **[Hongkong Post 香港郵政](http://www.hongkongpost.hk)**
    * Hongkong Post Root CA
        * SHA-1 is `E0925E18C7765E22DABD9427529DA6AF4E066428`
    * Hongkong Post Root CA 1
        * SHA-1 is `D6DAA8208D09D2154D24B52FCB346EB258B28A58`
    * **[Macao Post eSignTrust Certification Services](http://www.esigntrust.com)**
    * Macao Post eSignTrust Root Certification Authority
        * SHA-1 is `89C32E6B524E4D65388B9ECEDC637134ED4193A3`
    * Macao Post eSignTrust Root Certification Authority(G02)
        * SHA-1 is `06143151E02B45DDBADD5D8E56530DAAE328CF90`
    * **[中華電信公開金鑰基礎建設](http://epki.com.tw)**
    * ePKI Root Certification Authority
        * SHA-1 is `67650DF17E8E7E5B8240A4F4564BCFE23D69C6F0`
    * **[Government Root Certification Authority, GRCA](http://grca.nat.gov.tw/GRCAeng/htdocs/index.html)**
    * Government Root Certification Authority
        * SHA-1 is `F48B11BFDEABBE94542071E641DE6BBE882B40B9`
    * **[TWCA - 臺灣網路認證](http://www.twca.com.tw/Portal/Portal.aspx)**
    * TWCA Global Root CA
        * SHA-1 is `9CBB4853F6A4F6D352A4E83252556013F5ADAF65`
    * TWCA Root Certification Authority(1)
        * SHA-1 is `CF9E876DD3EBFC422697A3B5A37AA076A9062348`
    * TWCA Root Certification Authority(2)
        * SHA-1 is `DF646DCB7B0FD3A96AEE88C64E2D676711FF9D5F`
    * TaiCA Secure CA
        * SHA-1 is `5B404B6DB43E1F71557F75552E7668289B1B6309`
        * Intermediate certificate of GTE CyberTrust Global Root
    * TWCA Secure CA
        * SHA-1 is `3F3E6C4B33802A2FEA46C5CACA14770A40018899`
        * Intermediate certificate of Baltimore CyberTrust Root
    * TWCA Secure Certification Authority
        * SHA-1 is `339D811FEC673E7F731307A34C7C7523ABBE7DFE`
        * Intermediate certificate of AddTrust External CA Root