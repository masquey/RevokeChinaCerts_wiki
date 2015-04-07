### 使用方法
* 直接運行 `RevokeChinaCerts_Organization.bat` 並根據提示操作即可
* `Set force` 為證書強制策略，啟用後將強制檢查證書的使用，在不啟用 UAC 的情況也不能運行被吊銷證書的軟體。注意添加的工具需要 Microsoft .NET Framework 4.0+ 的支援，以及需要以管理員許可權運行

### 批次處理/腳本類型
* **Choice/提示選擇版本**：可由使用者根據提示自行選擇需要吊銷清單中代碼簽名的證書，**建議使用此版本**
* **All/完全版本**：吊銷了所有清單中代碼簽名的證書
* **Restore/恢復批次處理**：可恢復所有在上面幾個版本中所有被加入吊銷清單的證書的使用
* 代碼簽章憑證清單參見下文涉及的證書的介紹

### 涉及的證書
參見 https://github.com/chengr28/RevokeChinaCerts/blob/master/Windows/Certificates/Organization/Organization.md
