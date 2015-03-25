### 使用方法
* 直接運行 `RevokeChinaCerts_Organization.bat` 並根據提示操作即可
* `Set force` 為證書強制策略，啟用後將強制檢查證書的使用，在不啟用 UAC 的情況也不能運行被吊銷證書的軟體。注意添加的工具需要 Microsoft .NET Framework 4.0+ 的支援，以及需要以管理員許可權運行

### 批次處理/腳本類型
* **Choice/提示選擇版本**：可由使用者根據提示自行選擇需要吊銷清單中代碼簽名的證書，**建議使用此版本**
* **All/完全版本**：吊銷了所有清單中代碼簽名的證書
* **Restore/恢復批次處理**：可恢復所有在上面幾個版本中所有被加入吊銷清單的證書的使用
* 代碼簽章憑證清單參見下文涉及的證書的介紹

### 涉及的證書
* **所屬 [Agricultural Bank of China/ABC/中国农业银行](http://www.abchina.com)**
    * ABC
        * SHA1 `78D0CDF5752D1E5B58A674644CFE3499BF02F9EF`
    * ABC TEST CA
        * SHA1 `F18C39F8B5A3E9BADC811BBA7690E8D0143BD851`
    * ABC2048
        * SHA1 `6FAE9AD81467C5FCB93574670F52C8EF538F8B6D`
* **所屬 [Alibaba.com/阿里巴巴](http://www.alibaba.com)**
    * Alibaba.com Corporation Root CA
        * SHA1 `A7217F919843199C958C128449DD52D2723B0A8A`
    * ALIPAY_ROOT
        * SHA1 `59864294A96B3E5C37C058E9D1FBDE5FF0C2E4EE`
    * Alipay Trust NetWork
        * SHA1 `89A2FB0E332BA7275FE712FEC669D746125B1F32`
* **所屬 [Bank of Communications/BOC/中国交通银行](http://www.bankcomm.com)**
    * BOCOMCA
        * SHA1 `4571466B830EAC5FCDC22103B9733C1A15CE78AC`
* **所屬 [China Construction Bank/CCB/中国建设银行](http://www.ccb.com)**
    * CCB CA ROOT(1999-06-29)
        * SHA1 `3018E5D74DF29E3590F5BB8DF01AA7FC116BB4DE`
    * CCB CA ROOT(2009-06-01)
        * SHA1 `8582B4AF7491B3D16636EEB32D44993D7DEE6C40`
* **所屬 [China Financial Certification Authority/CFCA/中国金融认证中心](http://www.cfca.com.cn)**
    * CFCA
        * SHA1 `A9743B713E4109381622D3689AB5D9E1DC51B164`
    * CFCA CS CA
        * SHA1 `D3FBFAA8A67FC9A2EADBF86AEB5D07A9D6AF322E`
    * CFCA CS TEST CA
        * SHA1 `B5DCF1C58E86DBED2EA2D217A5C28D11FD9254F0`
    * CFCA Operation CA3
        * SHA1 `5A3A3EA74AE5D29F25A670024949869D1222E42A`
    * CFCA RCA
        * SHA1 `AE73DFF81CF24E50DD52CA1496E7EF94876061CB`
    * CFCA Root CA
        * SHA1 `31BD6AEF73031C5A49338E7A06040DD815EF7512`
    * CFCA RSA RCA
        * SHA1 `57C5CEBB53FBF181E0B13977AF864F1C13F11AA9`
* **所屬 [iTrusChina/天威诚信数字认证中心](http://www.itrus.com.cn)**
    * China Trust Network(1)
        * SHA1 `C2CAEB0DC296FD50596BCA0F53C5364521167039`
    * China Trust Network(2)
        * SHA1 `B39B0B24B156D8B6123CAF7BA249DC81F27E39FA`
    * China Trust Network(3)
        * SHA1 `7C88AE178AE6AB8E69C30AF586D84EF29B6E6AE3`
    * iTruschina CN Root CA(1)
        * SHA1 `240A61A2577970625B9F0B81283C4AA4037217B1`
    * iTruschina CN Root CA(2)
        * SHA1 `46F168AF009C28C18F452EB85F5E8747892B3C8B`
    * iTruschina CN Root CA(3)
        * SHA1 `654E9FADD2032AE1B87D6263AF04FD7FEE38D57C`
* **所屬 [Industrial and Commercial Bank of ChinaICBC/中国工商银行](www.icbc.com.cn)**
    * ICBC
        * SHA1 `E3F9043072BABF5E9C631960B34CCCF9FFC8BA41`
    * ICBC Root CA
        * SHA1 `5A960203C10CFA8D42DD115B61154F98E2F617F7`
    * IcbcCA
        * SHA1 `A02A23D13576ECA35498DC69166A20651E203E31`
    * Personal ICBC CA
        * SHA1 `2ABC81B0D7D052F887965562BB10AA66A80F7674`
* **所屬 [State Cryptography Administration Office of Security Commercial Code Administration/OSSCA/国家商用密码管理办公室](www.oscca.gov.cn)**
    * ROOTCA OSCCA
        * SHA1 `DBB84423C928ABE889D0E368FC3191D151DDB1AB`
* **所屬 [SZCA/深圳数字证书认证服务机构](http://www.szca.net)**
    * SZCA
        * SHA1 `B0049D436F27237EE59C746A1EF3C96A8E1B54AC`
    * SZCA(20030722)
        * SHA1 `90D7A97592F0A3E2165DE5DA23B57701D74A298D`
* **所屬 [TenpayCom/财付通](http://www.tenpay.com)**
    * TenpayCom Root CA
        * SHA1 `56502166C0DE2488950491C90C7560E0E7AA7378`
* **所屬 [吉林省数字证书认证中心](http://www.jlca.com.cn)**
    * AnXin CA Root
        * SHA1 `1D4A2E58C68F3F2D2659BC3BAB05CFA81F87B1E8`
* **所屬 [北京数字认证股份有限公司](http://www.bjca.org.cn)**
    * BeiJing ROOT CA
        * SHA1 `EC98F4A5096282FB192FFB168A574236C5A7DC6C`
* **所屬 [西部安全认证中心有限责任公司](http://www.cwca.com.cn)**
    * CWCA(2007-12-24)
        * SHA1 `029A0990DC0B34838A6AAC9662A9A5E23DD7B554`
    * CWCA(2013-01-18)
        * SHA1 `5A48E00BE8C9F33BDCAE3F61700675B4A3A3B6F3`
* **所屬 [福建省数字安全证书管理有限公司](http://www.fjca.com.cn)**
    * FJCA
        * SHA1 `DD9DE879188E29AE9C6CEF546D6191B89A6B4F09`
* **所屬 [GFAPKI](http://www.gfapki.com.cn)**
    * GFA CA CERTIFICATE
        * SHA1 `A4BF39D18409E9F27B8833543E56B9434A603CFF`
    * ROOT CERTIFICATE FOR GFA TRUST NETWORK(2007-01-11)
        * SHA1 `C49ED789F979213F0096060DF131B04EAADAC921`
    * ROOT CERTIFICATE FOR GFA TRUST NETWORK(2015-05-07)
        * SHA1 `C2859A597104BFC25B52EC15899A1999738AE13F`
* **所屬 [广西壮族自治区数字证书认证中心有限公司](http://www.gxca.com.cn)**
    * UTrust Root CA
        * SHA1 `5070A0E2FA1DB04C2ED63461ECE36307AB3A863B`
    * Guangxi ROOT CA
        * SHA1 `B3FAACDA0FFE817C3FC25B8D35FEC05A92314BDC`
* **所屬 [湖北省数字证书认证管理中心有限公司](http://www.hbca.org.cn)**
    * HBCA
        * SHA1 `E67291FCE01AB748D5E473F5CA1C3915A7EC5C8E`
* **所屬 [河南省数字证书认证中心](http://www.9611111.com)**
    * HNCA(2003-12-01)
        * SHA1 `3FF4124C794A11A26B49A14D005FD6D2BA5878F8`
    * HNCA(2013-08-21)
        * SHA1 `DAB0CA93310A2507A7407F4879BA56D105AAD3C2`
* **所屬 [江苏省电子商务服务中心](http://www.jsca.com.cn)**
    * JSCA_ROOT(1)
        * SHA1 `AA90ABA1EFA49F42772C7722F5A73A1C3936B811`
    * JSCA_ROOT(2)
        * SHA1 `4389F7886936C6B6D5532562CBB5DA5B4DD2296B`
* **所屬 [江西省数字证书有限公司](http://www.jxca.org.cn)**
    * JXCA
        * SHA1 `7A538FBBDE8EFDC125700718CC9B4A4BD9BA17E8`
* **所屬 [广东省电子商务认证有限公司](http://www.cnca.net)**
    * NETCA Root ClassA
        * SHA1 `2F6D7583B2CFD0F87698FB392C8B481058A280FB`
* **所屬 [培华校园云](http://dns.peihua.cn)**
    * Peihua-CA
        * SHA1 `82C5EAF859B5857D5DECD1BE6491E34E582D5BD8`
* **所屬 [山西省数字证书认证中心_山西CA_数字证书_数字签名_电子签名](http://www.sxca.com.cn)**
    * ShanXi Digital Certificate Authority
        * SHA1 `10CF1AAD52AE48E1249F9718C3DCF8FB27B12BF6`
* **所屬 [天津市电子认证中心](http://www.tjca.org.cn)**
    * TianJinROOT
        * SHA1 `53826F5DEF4E3AD9FD73DCF1D04E110D6DF7FDD6`
* **所屬 [新疆数字证书认证中心](http://www.xjca.com.cn)**
    * XjcaRoot
        * SHA1 `52A213B3CA8A5A5664D1BB9CF7A6A546C4E55973`
* **所屬 [浙江省数字安全证书管理有限公司](http://www.zjca.com.cn)**
    * ZJRoot
        * SHA1 `D65F531088EF11DD9BFA2BE437C906D44F9E9659`
* **所屬 [eID 公民网络电子身份标识](https://eid.cn)**
    * eID MICRoot
        * SHA1 `6F5C880129BED8B05B14C391364FE5298E2ED5FA`
