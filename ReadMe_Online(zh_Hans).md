### 使用方法
* **以管理员权限运行**批处理，并根据提示操作即可(Windows)：
    * `RevokeChinaCerts_Online.bat` - 系统内置证书列表
    * `RevokeChinaCerts_Firefox.bat` - Firefox 浏览器
    * 如需同时禁用，则需要分别运行批处理
* 其它平台的全自动工具吊销的方法，参见各平台目录页面的介绍
* **操作完毕后请务必清空所有浏览器数据和系统缓存**，并建议重启网络连接

### 批处理/脚本类型
* **1** 为 **Base/基础版本**：删除信任并吊销了几个可疑的根证书、中级证书或假证书
* **2** 为 **Extended/扩展版本**：删除信任并吊销了所有可疑的根证书、中级证书或假证书
    * **建议使用此版本**
* **3** 为 **All/完全版本**：删除信任并吊销了所有可疑的来自大中华地区的证书
    * **此版本用于测试不建议使用**
* **4** 为 **Restore/恢复版本**：可恢复所有在上面几个版本中所有被加入吊销列表的证书的使用

### 特別提醒
* **部分安全软件的 HTTPS 扫描功能可能会利用中间人攻击的方法自己签发 CA 证书对加密内容进行扫描，此类功能会直接导致本工具完全失效，强烈建议关闭此类功能或者将其彻底卸载！**
* **Extended** 版和 **All** 版会自动吊销 GoAgent 自带的 `GoAgent CA` 证书，为免使用 GoAgent 时出现错误同时也为了系统加密连接的安全强烈建议更换其自带的 CA 根证书。**关闭所有 GoAgent 程序，进入其 `local` 目录删除 `CA.crt` 以及整个 `certs` 目录，然后清空所有浏览器数据重启 GoAgent 和浏览器即可。**

### Windows 系统注意事项
* 本工具先将列表中的证书删除，再将这些证书添加到 CRL 证书吊销列表中，在 CRL 证书吊销列表中的证书才能被彻底禁用。**直接将 CTL 证书信任列表中的证书删除并没有任何作用，下次访问使用该证书的网站时会重新自动联网添加！**
* 大部分程序和 Chrome 以及 Opera 浏览器均使用系统内置提供的证书列表
* **Firefox** 中对自带根证书执行 `删除或不信任` 操作就相当于是禁用其所有目的，并不会将根证书本身删除
* 遇到错误 `Error: Can not find a certificate matching the hash value` 为正常现象，只要添加吊销证书时出现 `CertMgr Succeeded` 并通过实际访问网站测试即可
* 遇到错误 `Failed to save to the destination store` 可能为对应权限错误，要对当前用户的证书列表进行修改必须不能使用管理员权限，要对计算机全局证书列表进行修改必须使用管理员权限
* 遇到错误 `Error: Failed to add or delete certificates` 可能为由于证书列表为空 CertMgr 程序操作错误导致

### Windows 系统证书列表升级
* **1** 为升级 **CRL/证书吊销列表**
* **2** 为通过 **SST** 数据库的方法升级 **CTL/证书信任列表**
* **3** 为通过 RootSUPD 证书更新补丁升级 CTL/证书信任列表**（已结束支持）**
* **4** 为重置 **CRL/证书吊销列表**
* 要重置对CTL/证书信任列表的更改，需要运行 Microsoft Fixit 工具并重启系统：
    * **Microsoft_Fixit_20135.diagcab** - 适用于 Windows Vista 以及更新的版本
    * **Microsoft_Fixit_51014.msi** - 适用于 Windows XP/2003 以及以前的版本
* 数据库的长期更新：
    * SST 数据库可通过 [KB2677070/An automatic updater of revoked certificates is available](https://support.microsoft.com/en-us/kb/2677070) 中提供的地址获取，得到的 CAB -> STL 证书列表可通过系统自带的 Certutil 工具使用 `generateSSTFromWU` 和 `syncWithWU` 参数下载到含有证书本体的 SST 数据库，其可供 Certmgr 直接使用。具体情况参见 [Configure Trusted Roots and Disallowed Certificates](https://technet.microsoft.com/en-us/library/dn265983.aspx)
    * [KB931125/RootSUPD](https://support.microsoft.com/en-us/kb/931125) 随着对 Windows XP 支持期的结束，可能不再会有更新

### 其它平台非全自动工具吊销方法
* **Linux**(以 Debian 系为例，其它 Linux 发行版操作方法参见其官方说明)
    * 打开终端并执行 `sudo dpkg-reconfigure ca-certificates`
    * 在列表中找到并选择需要禁用的证书，按空格键取消对该证书的信任
    * 对所有需要禁用的证书执行完上步操作后回车确定
    * 操作完毕建议清空所有浏览器数据和系统缓存，并重启网络连接
* **Mac**
    * `实用工具` - `钥匙串访问` - 在 `钥匙串` 中选择 `系统根证书`
    * 点击进入需要禁用的证书，展开 `信任` 标签并在 `使用此证书时` 下拉菜单选择 `永不信任` 并关闭即可
    * 操作完毕建议清空所有浏览器数据和系统缓存，并重启网络连接
* **Firefox**
    * `工具` - `选项` - `高级` - `证书` - `查看证书`
    * 点击进入需要禁用的证书，直接点击 `删除或不信任` 按钮即可
    * 操作完毕建议清空所有浏览器数据和系统缓存，并重启网络连接
* **Android**
    * `设置` - `安全` - `受信任的凭据(显示受信任的CA证书)`
    * 点击进入需要禁用的证书并下拉到最下面，点击 `禁用` 按钮即可
    * 操作完毕建议清空所有浏览器数据和系统缓存，并重启网络连接
* **iOS** 没有任何官方渠道禁用自带的根证书，请放弃在 iOS 下禁用根证书的想法

### 涉及的证书
参见 https://github.com/chengr28/RevokeChinaCerts/wiki/ReadMe_Online#about-certificates