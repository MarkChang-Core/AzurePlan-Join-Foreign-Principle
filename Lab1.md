## Azure Plan - 經銷商加入 Foreign Principle

### 事前準備

以下資訊必須事前完成蒐集與準備 -

- **Azure Az Powershell Module 與 .NET Framework 4.7 -**

  請先確認操作的電腦已安裝 .NET Framework 4.7，且Powershell已安裝Azure Az PowerShell module，關於安裝請參考[這裡](https://docs.microsoft.com/zh-tw/powershell/azure/install-az-ps?view=azps-6.4.0)

- **安裝Az.Resource Module -**
  ```
  Install-Module -Name Az.Resources -Force -Verbose
  Import-Module -Name Az.Resources -Verbose -MinimumVersion 4.1.1!
  ```
  
- **Azure Subscription Account Owner -**

  需具備一組於於客戶的Azure Subsciption Account為Owner角色的登入帳號與密碼，關於如此新增Owner，請點選[這裡](https://github.com/MarkChang-Core/AzurePlan-Join-Foreign-Principle/blob/main/Lab1-1.md)

- **AdminAgents Object ID -**

  需查詢到Partner Center 的 AdminAgents Object ID，如何查詢請點選[這裡](https://github.com/MarkChang-Core/AzurePlan-Join-Foreign-Principle/blob/main/Lab1-2.md)

- **Azure Subscription Account ID -**

  請登入客戶端Azure Portal後，點擊由CSP創建的Azure Subscription Account，並於「概觀」中找到「訂用帳戶ID」

---------------------------------------

### 操作加入 Foreign Principle

請先確認接下來操作登入的帳號於客戶的Azure Subscription Account中，具備有「Owner」的權限。

同時也請確認已完成蒐集「AdminAgents Object ID」、「Azure Subscription Account ID」

並且操作的PC已安裝完成 .NET Frameworkk 4.7以上版本、Powershell也完成各項Module的安裝。

</br>
</br>

Step 1. 請先以系統管理員身分開啟Powershell，並輸入以下指令登入Azure Account -

```
Connect-AzAccount
```

![GITHUB](https://github.com/MarkChang-Core/AzurePlan-Join-Foreign-Principle/blob/main/image/image1.jpg)<br>

Step 2. 接者將登入的帳號切換至客戶的Azure Subscription Account，請輸入以下指令進行 -

```
Set-AzContext -SubscriptionId AzureSubscriptionAccountID
```

※ 其中 _AzureSubscriptionAccountID_ 請更換為客戶的Azure Subscription Account ID

![GITHUB](https://github.com/MarkChang-Core/AzurePlan-Join-Foreign-Principle/blob/main/image/image2.jpg)<br>

Step 3. 最後請輸入以下指令將間接經銷商以Foreign Principle身分加入客戶的Azure Subscription Account成為Owner -

```
New-AzRoleAssignment -ObjectId AdminAgentsObjectID -RoleDefinitionName "Owner" -Scope "/subscriptions/AzureSubscriptionAccountID" -ObjectType "ForeignGroup"
```

※ 其中，_AdminAgentsObjectID_ 請更換為 [事前準備](https://github.com/MarkChang-Core/AzurePlan-Join-Foreign-Principle/blob/main/Lab1.md#%E4%BA%8B%E5%89%8D%E6%BA%96%E5%82%99) 中的AdminAgents Object ID

※ 其中，_AzureSubscriptionAccountID_ 請更換為 [事前準備](https://github.com/MarkChang-Core/AzurePlan-Join-Foreign-Principle/blob/main/Lab1.md#%E4%BA%8B%E5%89%8D%E6%BA%96%E5%82%99) 中的Azure Subscription Account ID

![GITHUB](https://github.com/MarkChang-Core/AzurePlan-Join-Foreign-Principle/blob/main/image/image3.jpg)<br>

---------------------------------------

### 驗證是否已加入成功

- 於Azure Subscription Account > IAM 中查看角色

![GITHUB](https://github.com/MarkChang-Core/AzurePlan-Join-Foreign-Principle/blob/main/image/image4.jpg)<br>

- 於Partner Center中搜尋到客戶名稱，並於 Service Management > Microsoft Azure Management Portal 嘗試登入查看

