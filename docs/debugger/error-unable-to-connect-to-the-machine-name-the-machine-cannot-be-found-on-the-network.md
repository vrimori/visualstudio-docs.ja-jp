---
title: "エラー: コンピューター &lt;name&gt; に接続できません。このコンピューターはネットワーク上に見つかりません。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.remote.dcom_disabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DCOM, 接続できないエラー"
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# エラー: コンピューター &lt;name&gt; に接続できません。このコンピューターはネットワーク上に見つかりません。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このエラーは、次の条件のいずれかが満たされると発生します。  
  
-   リモート コンピューターへの接続が解除された。  
  
-   リモート コンピューターのユーザー アカウントが無効になっている。  
  
-   リモート コンピューターのパスワードの有効期限が切れている。  
  
### この問題を解決するには  
  
-   ローカル コンピューターとリモート コンピューターが同じネットワーク上に存在することを確認します。  これを行うには、Microsoft Windows エクスプローラー \(ファイル エクスプローラー\) を使用してリモート コンピューターにアクセスしてみます。  
  
     および  
  
-   リモート コンピューターへの接続に使用しているユーザー アカウントが有効になっていることを確認します。  
  
     および  
  
-   リモート コンピューターへの接続に使用しているパスワードが有効であり、有効期限が切れていないことを確認します。  
  
## 参照  
 [デバイスのリモート ツールのセットアップ](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [デバッグの設定と準備](../debugger/debugger-settings-and-preparation.md)