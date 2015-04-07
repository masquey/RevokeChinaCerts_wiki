### 使用方法
* 直接运行 `RevokeChinaCerts_Organization.bat` 并根据提示操作即可
* `Set force` 为证书强制策略，启用后将强制检查证书的使用，在不启用 UAC 的情况也不能运行被吊销证书的软件。注意添加的工具需要 Microsoft .NET Framework 4.0+ 的支持，以及需要以管理员权限运行

### 批处理/脚本类型
* **Choice/提示选择版本**：可由用户根据提示自行选择需要吊销列表中代码签名的证书，**建议使用此版本**
* **All/完全版本**：吊销了所有列表中代码签名的证书
* **Restore/恢复批处理**：可恢复所有在上面几个版本中所有被加入吊销列表的证书的使用
* 代码签名证书列表参见下文涉及的证书的介绍

### 涉及的证书
参见 https://github.com/chengr28/RevokeChinaCerts/blob/master/Windows/Certificates/Organization/Organization.md