### Batch version(Windows)
* **Base** is the base version of AntiChinaCerts, which can revoke some root/intermediate/fake certificates.
* **Extended** is the extended version of AntiChinaCerts, which can revoke all root/intermediate/fake certificates. **This is the suggestion.**
* **All** is the all version of AntiChinaCerts, which can revoke all certificates from greater China. **This is the test version.**
* **Restore** is the restore batch, which can restore all revoked certificates.
* The list of certificates is in About Certificates section.

### Usage
* Windows
    * Choose the version and run `.bat` file.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Optional, but strongly recommended)
* Linux(Debian, other Linux distributions need to see its official description)
    * Execute `sudo dpkg-reconfigure ca-certificates` in terminal.
    * Using the space bar to revoke the certifications.
    * Using enter key to save changes.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Optional, but strongly recommended)
* Mac
    * Using shell script
        * Get the root permission with `sudo` and run `AntiChinaCerts.sh`.
    * Manually
        * Open `Utilities` - `Keychain Access` - `Keychains` - `System Roots`
        * Open the certification and select all `Not trusted`.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Optional, but strongly recommended)
* Firefox
    * Open `Tools` - `Options` - `Advanced` - `Certificates` - `View Certificates`
    * Open the certification and select to disable.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Optional, but strongly recommended)
* Android
    * `Setting` - `Security` - `Trusted credentials`
    * Open the certification and select `Disable`.
    * Clear all browser(s) data and DNS cache of system, then restart network interface(s). (Optional, but strongly recommended)

### Explanation
* Windows
    * Delete certification can not revoke it. You must add the certification to CRL to disable it(or call Revoke).
    * Most of Windows programs, Chrome and Opera is using system certification list.
* Linux
    * Different Linux distributions need different process, see its official description.
* Mac
    * `CNNIC ROOT`, `China Internet Network Information Center EV Certificates Root`, `UCA Global Root` and `UCA Root` in OS X 10.9.
* Firefox
    * `CNNIC ROOT` and `China Internet Network Information Center EV Certificates Root` in Firefox 32.
* Android
    * `CNNIC ROOT` and `China Internet Network Information Center EV Certificates Root` in Android 4.4.4.

### Attention
* Windows
    * You must run the revoking or restoring batch in all users in Windows.
* Android
    * Pay attention to any certification errors, it can be ignored in Android.
    * Android not trust certifications which are not in list of system.
* iOS
    * There are not any ways(Undocumented) to revoke system roots in iOS.

### About Certifications
* **Base version**
    * Fake GitHub.Com(2013-01-25)
        * SHA-1 fingerprint is 27A29C3A8B3261770E8B59448557DC9E9339E68C
        * This fake certification is used for man-in-the-middle attacking GitHub in 2013-01-25.
    * Fake Google.Com(2014-07-24)
        * SHA-1 fingerprint is F6BEADB9BC02E0A152D71C318739CDECFC1C085D
        * This fake certification is used for man-in-the-middle attacking Google in 2014-09-01.
    * Fake Google.Com(2014-09-18)
        * SHA-1 fingerprint is 316076F2866588DBB233C7F9EB68B58125150C21
        * This fake certification is used for man-in-the-middle attacking Google when using IPv6 tunneling in October, 2014.
    * Fake Yahoo.Com(2014-09-23)
        * SHA-1 fingerprint is 2290C311EA0F3F57E06DF45B698E18E828E59BC3
        * This fake certification is used for man-in-the-middle attacking Yahoo in 2014-09-30.
    * Fake Hotmai.Com(2014-10-02)
        * SHA-1 fingerprint is 30F3B3ADC6E570BDA606B9F96DE24190CE262C67
        * This fake certification is used for man-in-the-middle attacking Microsoft in 2014-10-02.
    * Fake Www.Facebook.Com(2014-10-08)
        * SHA-1 fingerprint is DC6EE6EDC4C078E1B2C12F6D1985000E27CFD318
        * This fake certification is used for man-in-the-middle attacking Facebook when using CERNET IPv6 or IPv6 tunneling in 2014-10-08.
    * Fake Www.Icloud.Com(2014-10-04)
        * SHA-1 fingerprint is F468B5F3FED807974476A22B32EA3137D924F7BA
        * This fake certification is used for man-in-the-middle attacking Apple iCloud in 2014-10-18.
    * CNNIC ROOT
        * SHA-1 fingerprint is 8BAF4C9B1DF02A92F7DA128EB91BACF498604B6F
        * It's belong to [China Internet Network Information Center/CNNIC/中国互联网络信息中心](http://www.cnnic.net.cn)
        * [Test site](https://www.cnnic.net.cn)
    * China Internet Network Information Center EV Certificates Root
        * SHA-1 fingerprint is 4F99AA93FB2BD13726A1994ACE7FF005F2935D1E
        * It's belong to [China Internet Network Information Center/CNNIC/中国互联网络信息中心](http://www.cnnic.net.cn)
        * [Test site](https://evdemo.cnnic.cn)
    * CNNIC SSL
        * SHA-1 fingerprint is 6856BB1A6C4F76DACA362187CC2CCD484EDDC25D
        * Intermediate certification of Entrust.net Secure Server Certification Authority
        * Old CNNIC SSL certification which begin to available in 2007-05-11 and 2012-03-01 expired.
        * It's belong to [China Internet Network Information Center/CNNIC/中国互联网络信息中心](http://www.cnnic.net.cn)
* **Extended version**
    * CFCA GT CA
        * SHA-1 fingerprint is EABDA240440ABBD694930A01D09764C6C2D77966
        * Begin to available in 2011-06-13.
        * It's belong to [China Financial Certification Authority/CFCA/中国金融认证中心](http://www.cfca.com.cn)
        * [Test site](https://cstest.cfca.com.cn)
    * CFCA GT CA
        * SHA-1 fingerprint is A8F2DFE36AE0CC2DB9DD38347D30AED9551DD25A
        * Begin to available in 2012-08-21.
        * It's belong to [China Financial Certification Authority/CFCA/中国金融认证中心](http://www.cfca.com.cn)
    * CFCA EV ROOT
        * SHA-1 fingerprint is E2B8294B5584AB6B58C290466CAC3FB8398F8483
        * It's belong to [China Financial Certification Authority/CFCA/中国金融认证中心](http://www.cfca.com.cn)
        * [Test site](https://cs.cfca.com.cn)
    * UCA Global Root
        * SHA-1 fingerprint is 0B972C9EA6E7CC58D93B20BF71EC412E7209FABF
        * It's belong to [Shanghai Electronic Certificate Authority Center/SHECA/上海市数字证书认证中心](http://www.sheca.com)
        * [Test site](https://www.sheca.com)
    * UCA Root
        * SHA-1 fingerprint is 8250BED5A214433A66377CBC10EF83F669DA3A67
        * It's belong to [Shanghai Electronic Certificate Authority Center/SHECA/上海市数字证书认证中心](http://www.sheca.com)
        * [Test site](https://ibanks.bankofshanghai.com)
    * UCA Extended Validation Root
        * SHA-1 fingerprint is B9C9F58B3BBEF575E2B58328770E7B0076C40B5E
        * It's belong to [Shanghai Electronic Certificate Authority Center/SHECA/上海市数字证书认证中心](http://www.sheca.com)
    * UCA ROOT
        * SHA-1 fingerprint is 3120F295417730075F8CD42D0CAE008EB5726EF8
        * Old UCA ROOT certification which begin to available in 2001-01-01 and 2013-01-01 expired.
        * It's belong to [Shanghai Electronic Certificate Authority Center/SHECA/上海市数字证书认证中心](http://www.sheca.com)
        * [Test site](https://ibanks.bankofshanghai.com)
    * GoAgent CA
        * SHA-1 fingerprint is AB702CDF18EBE8B438C52869CD4A5DEF48B40E33
        * It's the default certification of [GoAgent](https://github.com/goagent/goagent).
* **All version**
    * ROOTCA
        * SHA-1 fingerprint is DBB84423C928ABE889D0E368FC3191D151DDB1AB
        * It's belong to [Office of the State Commercial Cryptography Administration/OSCCA/国家商用密码管理办公室](http://www.oscca.gov.cn)
    * SRCA
        * SHA-1 fingerprint is AE3F2E66D48FC6BD1DF131E89D768D505DF14302
        * It's belong to [Sinorail Certification Authority/SRCA/中铁数字证书认证中心](http://www.12306.cn)
        * [Test site](https://kyfw.12306.cn)
    * Certification Authority of WoSign
        * SHA-1 fingerprint is B94294BF91EA8FB64BE61097C7FB001359B676CB
        * It's belong to [沃通CA](http://www.wosign.com)
        * [Test site](https://www.wosign.com)
    * CA 沃通根证书
        * SHA-1 fingerprint is 1632478D89F9213A92008563F5A4A7D312408AD6
        * It's belong to [沃通CA](http://www.wosign.com)
    * Class 1 Primary CA
        * SHA-1 fingerprint is 6A174570A916FBE84453EED3D070A1D8DA442829
        * Old WoSign(USA) certification which begin to available in 1999-07-08 and 2020-07-07 expired.
        * It's belong to [沃通CA](http://www.wosign.com)
    * Certification Authority of WoSign
        * SHA-1 fingerprint is 868241C8B85AF79E2DAC79EDADB723E82A36AFC3
        * Intermediate certification of StartCom Certification Authority
        * It's belong to [沃通CA](http://www.wosign.com)
    * Certification Authority of WoSign
        * SHA-1 fingerprint is 56FAADDC596DCF78D585D83A35BC04B690D12736
        * Intermediate certification of UTN - DATACorp SGC
        * It's belong to [沃通CA](http://www.wosign.com)
    * WoSign Premium Server Authority
        * SHA-1 fingerprint is E3D569137E603E7BACB6BCC66AE943850C8ADF38
        * Intermediate certification of AddTrust External CA Root/UTN-USERFirst-Hardware
        * It's belong to [沃通CA](http://www.wosign.com)
    * WoSign Server Authority
        * SHA-1 fingerprint is 3E14B8BD6C568657D852D95D387249AE857B4A39
        * Intermediate certification of AddTrust External CA Root/UTN-USERFirst-Hardware
        * It's belong to [沃通CA](http://www.wosign.com)
    * WoSign SGC Server Authority
        * SHA-1 fingerprint is 6D5A18050D56BFDE525CBE89E8C45DD1B53D12E9
        * Intermediate certification of UTN - DATACorp SGC
        * It's belong to [沃通CA](http://www.wosign.com)
    * WoTrust Premium Server Authority
        * SHA-1 fingerprint is 381CBC5048AFD9A02D3E5882D5F22D962B1A5F72
        * Intermediate certification of AddTrust External CA Root/UTN-USERFirst-Hardware
        * It's belong to [沃通CA](http://www.wosign.com)
    * WoTrust Server Authority
        * SHA-1 fingerprint is 337DF96418F08A9355870513AFCEBDC68BCED767
        * Intermediate certification of AddTrust External CA Root/UTN-USERFirst-Hardware
        * It's belong to [沃通CA](http://www.wosign.com)
    * WoTrust SGC Server Authority
        * SHA-1 fingerprint is 46A762F3C3CF3732DE22A8BA1EBBA3BC048F9B8C
        * Intermediate certification of UTN - DATACorp SGC
        * It's belong to [沃通CA](http://www.wosign.com)
    * China Trust Network(1)
        * SHA-1 fingerprint is C2CAEB0DC296FD50596BCA0F53C5364521167039
        * It's belong to [iTrusChina/天威诚信数字认证中心](http://www.itrus.com.cn)
    * China Trust Network(2)
        * SHA-1 fingerprint is B39B0B24B156D8B6123CAF7BA249DC81F27E39FA
        * It's belong to [iTrusChina/天威诚信数字认证中心](http://www.itrus.com.cn)
    * China Trust Network(3)
        * SHA-1 fingerprint is 7C88AE178AE6AB8E69C30AF586D84EF29B6E6AE3
        * It's belong to [iTrusChina/天威诚信数字认证中心](http://www.itrus.com.cn)
    * Hongkong Post Root CA
        * SHA-1 fingerprint is E0925E18C7765E22DABD9427529DA6AF4E066428
        * Old Hongkong Post Root CA 1 certification which begin to available in 2000-01-16 and 2010-01-17 expired.
        * It's belong to [Hongkong Post 香港郵政](http://www.hongkongpost.hk)
    * Hongkong Post Root CA 1
        * SHA-1 fingerprint is D6DAA8208D09D2154D24B52FCB346EB258B28A58
        * It's belong to [Hongkong Post 香港郵政](http://www.hongkongpost.hk)
    * ePKI Root Certification Authority
        * SHA-1 fingerprint is 67650DF17E8E7E5B8240A4F4564BCFE23D69C6F0
        * It's belong to [中華電信公開金鑰基礎建設](http://epki.com.tw)
    * Government Root Certification Authority
        * SHA-1 fingerprint is F48B11BFDEABBE94542071E641DE6BBE882B40B9
        * It's belong to [Government Root Certification Authority, GRCA](http://grca.nat.gov.tw/GRCAeng/htdocs/index.html)
    * TWCA Global Root CA
        * SHA-1 fingerprint is 9CBB4853F6A4F6D352A4E83252556013F5ADAF65
        * It's belong to [TWCA - 臺灣網路認證](http://www.twca.com.tw/Portal/Portal.aspx)
    * TWCA Root Certification Authority(1)
        * SHA-1 fingerprint is CF9E876DD3EBFC422697A3B5A37AA076A9062348
        * It's belong to [TWCA - 臺灣網路認證](http://www.twca.com.tw/Portal/Portal.aspx)
    * TWCA Root Certification Authority(2)
        * SHA-1 fingerprint is DF646DCB7B0FD3A96AEE88C64E2D676711FF9D5F
        * It's belong to [TWCA - 臺灣網路認證](http://www.twca.com.tw/Portal/Portal.aspx)
    * TaiCA Secure CA
        * SHA-1 fingerprint is 5B404B6DB43E1F71557F75552E7668289B1B6309
        * Intermediate certification of GTE CyberTrust Global Root
        * It's belong to [TWCA - 臺灣網路認證](http://www.twca.com.tw/Portal/Portal.aspx)
    * TWCA Secure CA
        * SHA-1 fingerprint is 3F3E6C4B33802A2FEA46C5CACA14770A40018899
        * Intermediate certification of Baltimore CyberTrust Root
        * It's belong to [TWCA - 臺灣網路認證](http://www.twca.com.tw/Portal/Portal.aspx)
    * TWCA Secure Certification Authority
        * SHA-1 fingerprint is 339D811FEC673E7F731307A34C7C7523ABBE7DFE
        * Intermediate certification of AddTrust External CA Root
        * It's belong to [TWCA - 臺灣網路認證](http://www.twca.com.tw/Portal/Portal.aspx)
