## Azure Plan - 經銷商加入 Foreign Principle

當CSP協助建立Azure Plan(CPS v2)之後，通常將會CSP本身的Foreign Principle加入至Azure Plan訂用帳戶中成為IAM的Owner，

這時CSP可透過Microsoft Partner Center以Foreign Principle角色登入客戶的Azure Portal協助管理，

但間接經銷商卻經常不會進行主動加入的功能，因此經常間接經銷商協助客戶維運的方式均是額外建立一組帳號並加入IAM成為Owner，

但此方式對於間接經銷商將會造成不便，因為當客戶數量增加的時候，便會需要紀錄多組的登入帳號、密碼，若疏於管理更可能導致資安風險。

因此本篇文章主要協助間接經銷商將自己的Foreign Principle加入客戶的Azure Subscription Account中，

如此便可以類似代理登入的方式，統一透過Partner Center管理客戶。

開始進行Foreign Principle的新增，請前往[Lab 1](https://github.com/MarkChang-Core/AADC/blob/main/Lab1.md)。
