## Azure Plan - 經銷商加入 Foreign Principle

操作必要條件：已安裝 **Azure Az Powershell Module 與 .NET Framework 4.7**，關於安裝請參考[這裡](https://docs.microsoft.com/zh-tw/powershell/azure/install-az-ps?view=azps-6.4.0)

### 查詢Partner Center AdminAgents Object ID

Step1. 請先以系統管理員身分開啟Powershell，並輸入以下指令登入Azure Account -

```
Connect-AzAccount
```

![GITHUB](https://github.com/MarkChang-Core/AzurePlan-Join-Foreign-Principle/blob/main/image/image2-1.jpg)<br>

Step2. 輸入以下指令取得AdminAgents的Object ID，Object ID的位置於下圖紅框處 -

```
Get-AzADGroup -DisplayName AdminAgents
```

![GITHUB](https://github.com/MarkChang-Core/AzurePlan-Join-Foreign-Principle/blob/main/image/image2-2.jpg)<br>

等待確認到 Object ID之後，請[點擊](https://github.com/MarkChang-Core/AzurePlan-Join-Foreign-Principle/edit/main/Lab1.md)回到間接經銷商加入 Foreign Principle的操作流程以繼續操作。



