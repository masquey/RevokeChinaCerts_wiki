### 批次處理/腳本類型
* **Base** 為基礎版本，刪除信任並吊銷了幾個可疑的根憑證、中級證書或假證書，直接運行 `RevokeChinaCerts_Base.bat` 即可
* **Extended** 為擴展版本，刪除信任並吊銷了所有可疑的根憑證、中級證書或假證書，直接運行 `RevokeChinaCerts_Extended.bat` 即可，**建議使用此版本**
* **All** 為完全版本，刪除信任並吊銷了所有可疑的來自大中華地區的證書，直接運行 `RevokeChinaCerts_All.bat` 即可，**此版本用於測試不建議使用**
* **Restore** 為恢復批次處理，直接運行 `RevokeChinaCerts_Restore.bat` 可恢復所有在上面幾個版本中所有被加入吊銷清單的證書的使用
* 具體的根憑證、中級證書或假證書清單參見下文涉及的證書的介紹

### 特别提醒
* **Extended** 版和 **All** 版會自動吊銷 GoAgent 自帶的 `GoAgent CA` 證書，為免使用 GoAgent 時出現錯誤同時也為了系統加密連接的安全強烈建議更換其自帶的 CA 根憑證。**關閉所有 GoAgent 程式，進入其 `local` 目錄刪除 `CA.crt` 以及整個 `certs` 目錄，然後清空所有瀏覽器資料重啟 GoAgent 和瀏覽器即可。**

### 使用方法
* Windows
    * 選擇好不同的版本，直接運行位於 Windows 目錄裡的批次處理
    * 操作完畢建議清空所有瀏覽器資料和系統緩存，並重啟網路連接
* Linux
    * 以 Debian 系列為例，其它 Linux 發行版本操作方法參見其官方說明
    * 打開終端並執行 `sudo dpkg-reconfigure ca-certificates`
    * 在清單中找到並選擇需要禁用的證書，按空格鍵取消對該證書的信任
    * 對所有需要禁用的證書執行完上步操作後回車確定
    * 操作完畢建議清空所有瀏覽器資料和系統緩存，並重啟網路連接
* Mac
    * 使用自動腳本
        * 使用 `sudo` 以 ROOT 許可權運行位於 Mac 目錄裡的 `RevokeChinaCerts.sh` 或 `RevokeChinaCerts_All.sh` 即可
    * 手動操作
        * `公用程式` - `鑰匙串訪問` - 在 `鑰匙串` 中選擇 `系統根憑證`
        * 點擊進入需要禁用的證書，展開 `信任` 標籤並在 `使用此證書時` 下拉式功能表選擇 `永不信任` 並關閉即可
    * 操作完畢建議清空所有瀏覽器資料和系統緩存，並重啟網路連接
* Firefox
    * `工具` - `選項` - `高級` - `證書` - `查看證書`
    * 點擊進入需要禁用的證書，直接點擊 `刪除或不信任` 按鈕即可
    * 操作完畢建議清空所有瀏覽器資料和系統緩存，並重啟網路連接
* Android
    * `設置` - `安全` - `受信任的憑據(顯示受信任的CA證書)`
    * 點擊進入需要禁用的證書並下拉到最下面，點擊 `禁用` 按鈕即可
    * 操作完畢建議清空所有瀏覽器資料和系統緩存，並重啟網路連接

### 說明
* Windows
    * 本工具作用是先將清單中的證書刪掉，然後再將這些證書添加到CRL憑證撤銷清單中，CRL憑證撤銷清單中的證書才能被徹底禁用
    * 大部分 Windows 的程式和瀏覽器 Chrome 以及 Opera 亦使用 Windows 系統提供的證書清單
* Linux
    * 不同發行版本系統本身的CA根憑證清單可能有所不同，具體需要按實際情況操作
* Mac
    * OS X Yosemite 版本時經已自帶有 `CNNIC ROOT` 和 `China Internet Network Information Center EV Certificates Root` 和 `UCA Global Root` 以及 `UCA Root`
* Firefox
    * 32 版本時經已自帶有 `CNNIC ROOT` 以及 `China Internet Network Information Center EV Certificates Root`
* Android
    * 5.0.1 版本時經已自帶有 `CNNIC ROOT` 以及 `China Internet Network Information Center EV Certificates Root`

### 注意
* Windows
    * **直接將證書直接刪除並沒有任何作用，下次訪問使用該證書的網站時又會重新自動聯網添加。而由於每個使用者使用獨立的證書清單，需要所有使用者都運行一次本工具才能徹底禁用證書的使用！**
    * 運行時如果遇到 `Error: Can not find a certificate matching the hash value` 等不需要在意，只要後面吊銷證書時 `CertMgr Succeeded` 運行成功就行
* Linux
    * 在 `/usr/share/ca-certificates` 裡也有一份各程式自己的CA根憑證清單，大多數情況下直接刪除可能並不能禁用證書
    * Linux 發行版本系統雖然提供了 CA 根憑證調用的統一介面，但程式實際使用的 CA 根憑證清單可能是程式本身另外保存的一份，所以實際程式使用的 CA 根憑證清單可能與系統統一介面不相同，**強烈建議在系統統一介面禁用證書後再通過程式本身提供的證書管理器進行禁用**
* Firefox
    * 在 Firefox 裡對自帶根憑證執行 `刪除或不信任` 操作就相當於是禁用其所有目的，並不會將根憑證本身刪除
* Android
    * Android 上由於沒有提供比較方便的方法編輯CRL清單，故證書並不能被完全禁用，Apps 可以通過忽略證書錯誤繼續使用
    * Android 系統沒有自帶的CA根憑證預設為不信任狀態，不需要手動添加到系統中
* iOS
    * iOS 沒有任何官方提供的方法禁用自帶的根憑證，請放棄在 iOS 下禁用根憑證的想法

### 涉及的證書
* **Base 版本**
    * **以下證書均被用於大規模中間人攻擊**
    * Fake github.com(2013-01-25)
        * SHA-1 `27A29C3A8B3261770E8B59448557DC9E9339E68C`
        * 2013-01-25 大規模中間人攻擊 GitHub 網站
    * Fake google.com(2014-07-24)
        * SHA-1 `F6BEADB9BC02E0A152D71C318739CDECFC1C085D`
        * 2014-09-01 大規模中間人攻擊 Google 網站
    * Fake google.com(2014-09-18)
        * SHA-1 `316076F2866588DBB233C7F9EB68B58125150C21`
        * 2014-10 部分 IPv6 通道伺服器中間人攻擊 Google 網站
    * Fake yahoo.com(2014-09-23)
        * SHA-1 `2290C311EA0F3F57E06DF45B698E18E828E59BC3`
        * 2014-09-30 大規模中間人攻擊 Yahoo 網站
    * Fake hotmai.com(2014-10-02)
        * SHA-1 `30F3B3ADC6E570BDA606B9F96DE24190CE262C67`
        * 2014-10-02 大規模中間人攻擊 Microsoft 網站
    * Fake `www.facebook.com`(2014-10-08)
        * SHA-1 `DC6EE6EDC4C078E1B2C12F6D1985000E27CFD318`
        * 2014-10-08 部分教育網 IPv6 和通道伺服器中間人攻擊 Facebook 網站
    * Fake `www.icloud.com`(2014-10-04)
        * SHA-1 `F468B5F3FED807974476A22B32EA3137D924F7BA`
        * 2014-10-18 大規模中間人攻擊 Apple iCloud 網站
    * Fake *.hotmail.com(2015-01-17)
        * SHA-1 `75F411595FE9A21A17A4967C7B666E5152791A32`
        * 2015-01-17 大規模中間人攻擊 Hotmail 的 IMAP 協議
    * **以下證書均所屬 [China Internet Network Information Center/CNNIC/中国互联网络信息中心](http://www.cnnic.net.cn)**
    * CNNIC ROOT
        * SHA-1 `8BAF4C9B1DF02A92F7DA128EB91BACF498604B6F`
        * [測試網址](https://www.cnnic.net.cn)
    * China Internet Network Information Center EV Certificates Root
        * SHA-1 `4F99AA93FB2BD13726A1994ACE7FF005F2935D1E`
        * [測試網址](https://evdemo.cnnic.cn)
    * CNNIC SSL
        * SHA-1 `6856BB1A6C4F76DACA362187CC2CCD484EDDC25D`
        * 由 Entrust.net Secure Server Certification Authority 簽發的中級憑證授權單位
    * **所屬 [Baidu/百度公司](http://www.baidu.com)**
    * Baidu WACC service
        * SHA-1 `7514436E903C901069980499CA70DE74FC06C83C`
        * [測試網址](https://wacc.n.shifen.com)
    * **所屬 [Giant Interactive Group Inc./巨人网络](http://www.ztgame.com)**
    * GiantRootCA
        * SHA-1 `561422647B89BE22F203EBCAEF52B5007227510A`
        * [測試網址](https://mail.ztgame.com)
* **Extended 版本**
    * **以下證書均所屬 [China Financial Certification Authority/CFCA/中国金融认证中心](http://www.cfca.com.cn)**
    * CFCA GT CA
        * SHA-1 `EABDA240440ABBD694930A01D09764C6C2D77966`
    * CFCA GT CA
        * SHA-1 `A8F2DFE36AE0CC2DB9DD38347D30AED9551DD25A`
    * CFCA EV ROOT
        * SHA-1 `E2B8294B5584AB6B58C290466CAC3FB8398F8483`
        * [測試網址](https://cs.cfca.com.cn)
    * UCA Global Root
        * SHA-1 `0B972C9EA6E7CC58D93B20BF71EC412E7209FABF`
        * [測試網址](https://www.sheca.com)
    * UCA Root
        * SHA-1 `8250BED5A214433A66377CBC10EF83F669DA3A67`
        * [測試網址](https://ibanks.bankofshanghai.com)
    * UCA Extended Validation Root
        * SHA-1 `B9C9F58B3BBEF575E2B58328770E7B0076C40B5E`
    * UCA ROOT
        * SHA-1 `3120F295417730075F8CD42D0CAE008EB5726EF8`
        * [測試網址](https://ibanks.bankofshanghai.com)
    * **所屬 [GoAgent](https://github.com/goagent/goagent) 專案于初版使用至 3.2.0 的預設 CA 根憑證**
    * GoAgent CA
        * SHA-1 `AB702CDF18EBE8B438C52869CD4A5DEF48B40E33`
* **All 版本**
    * **所屬 [Sinorail Certification Authority/SRCA/中铁数字证书认证中心](http://www.12306.cn)**
    * SRCA
        * SHA-1 `AE3F2E66D48FC6BD1DF131E89D768D505DF14302`
        * [測試網址](https://kyfw.12306.cn)
    * **以下證書均所屬 [沃通CA](http://www.wosign.com)**
    * Certification Authority of WoSign
        * SHA-1 `B94294BF91EA8FB64BE61097C7FB001359B676CB`
    * CA 沃通根证书
        * SHA-1 `1632478D89F9213A92008563F5A4A7D312408AD6`
    * Class 1 Primary CA
        * SHA-1 `6A174570A916FBE84453EED3D070A1D8DA442829`
    * Certification Authority of WoSign
        * SHA-1 `33A4D8BC38608EF52EF0E28A35091E9250907FB9`
    * Certification Authority of WoSign
        * SHA-1 `868241C8B85AF79E2DAC79EDADB723E82A36AFC3`
        * 由 StartCom Certification Authority 簽發的中級憑證授權單位
    * Certification Authority of WoSign
        * SHA-1 `692790DA5189529CC5CE1E16E984277A03023E99`
        * 由 StartCom Certification Authority 簽發的中級憑證授權單位
    * Certification Authority of WoSign
        * SHA-1 `804E5FB7DE84F5F5B28347233EAF07846B6070D3`
        * 由 StartCom Certification Authority 簽發的中級憑證授權單位
    * CA 沃通根证书
        * SHA-1 `D8EFF6C28BB508E4702565F42748454A872BD412`
        * 由 StartCom Certification Authority 簽發的中級憑證授權單位
    * Certification Authority of WoSign
        * SHA-1 `56FAADDC596DCF78D585D83A35BC04B690D12736`
        * 由 UTN - DATACorp SGC 簽發的中級憑證授權單位
    * WoSign Premium Server Authority
        * SHA-1 `E3D569137E603E7BACB6BCC66AE943850C8ADF38`
        * 由 AddTrust External CA Root/UTN-USERFirst-Hardware 簽發的中級憑證授權單位
    * WoSign Server Authority
        * SHA-1 `3E14B8BD6C568657D852D95D387249AE857B4A39`
        * 由 AddTrust External CA Root/UTN-USERFirst-Hardware 簽發的中級憑證授權單位
    * WoSign SGC Server Authority
        * SHA-1 `6D5A18050D56BFDE525CBE89E8C45DD1B53D12E9`
        * 由 UTN - DATACorp SGC 簽發的中級憑證授權單位
    * WoSign Client Authority
        * SHA-1 `FAD4319D4E173FF3853E51C98D21919BF3DA1A1E`
        * 由 UTN-USERFirst-Client Authentication and Email 簽發的中級憑證授權單位
    * WoTrust Premium Server Authority
        * SHA-1 `381CBC5048AFD9A02D3E5882D5F22D962B1A5F72`
        * 由 AddTrust External CA Root/UTN-USERFirst-Hardware 簽發的中級憑證授權單位
    * WoTrust Server Authority
        * SHA-1 `337DF96418F08A9355870513AFCEBDC68BCED767`
        * 由 AddTrust External CA Root/UTN-USERFirst-Hardware 簽發的中級憑證授權單位
    * WoTrust SGC Server Authority
        * SHA-1 `46A762F3C3CF3732DE22A8BA1EBBA3BC048F9B8C`
        * 由 UTN - DATACorp SGC 簽發的中級憑證授權單位
    * WoTrust Client Authority
        * SHA-1 `38CFE78D9F1F0B0637AFCAAA3D5549D87C0AA1D0`
        * 由 UTN-USERFirst-Client Authentication and Email 簽發的中級憑證授權單位
    * **以下證書均所屬 [Hongkong Post 香港郵政](http://www.hongkongpost.hk)**
    * Hongkong Post Root CA
        * SHA-1 `E0925E18C7765E22DABD9427529DA6AF4E066428`
    * Hongkong Post Root CA 1
        * SHA-1 `D6DAA8208D09D2154D24B52FCB346EB258B28A58`
    * **以下證書均所屬 [Macao Post eSignTrust Certification Services](http://www.esigntrust.com)**
    * Macao Post eSignTrust Root Certification Authority
        * SHA-1 `89C32E6B524E4D65388B9ECEDC637134ED4193A3`
    * Macao Post eSignTrust Root Certification Authority(G02)
        * SHA-1 `06143151E02B45DDBADD5D8E56530DAAE328CF90`
    * **所屬 [中華電信公開金鑰基礎建設](http://epki.com.tw)**
    * ePKI Root Certification Authority
        * SHA-1 `67650DF17E8E7E5B8240A4F4564BCFE23D69C6F0`
    * **所屬 [Government Root Certification Authority, GRCA](http://grca.nat.gov.tw/GRCAeng/htdocs/index.html)**
    * Government Root Certification Authority
        * SHA-1 `F48B11BFDEABBE94542071E641DE6BBE882B40B9`
    * **以下證書均所屬 [TWCA - 臺灣網路認證](http://www.twca.com.tw/Portal/Portal.aspx)**
    * TWCA Global Root CA
        * SHA-1 `9CBB4853F6A4F6D352A4E83252556013F5ADAF65`
    * TWCA Root Certification Authority(1)
        * SHA-1 `CF9E876DD3EBFC422697A3B5A37AA076A9062348`
    * TWCA Root Certification Authority(2)
        * SHA-1 `DF646DCB7B0FD3A96AEE88C64E2D676711FF9D5F`
    * TaiCA Secure CA
        * SHA-1 `5B404B6DB43E1F71557F75552E7668289B1B6309`
        * 由 GTE CyberTrust Global Root 簽發的中級憑證授權單位
    * TWCA Secure CA
        * SHA-1 `3F3E6C4B33802A2FEA46C5CACA14770A40018899`
        * 由 Baltimore CyberTrust Root 簽發的中級憑證授權單位
    * TWCA Secure Certification Authority
        * SHA-1 `339D811FEC673E7F731307A34C7C7523ABBE7DFE`
        * 由 AddTrust External CA Root 簽發的中級憑證授權單位