---
title: "エラー : 認証を要求する RPC | Microsoft Docs"
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
  - "vs.debug.error.rpc_requires_authentication"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# エラー : 認証を要求する RPC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio デバッガーは、リモート コンピューターに接続できません。  リモート コンピューター上で、リモート デバッグを制限する RPC ポリシーが有効になっています。  
  
### このエラーを解決するには  
  
1.  `\` *windir* `\system32\regedt32.exe` を実行します。  
  
2.  `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` を見つけて削除します。  
  
3.  コンピューターを再起動してレジストリの変更を有効にします。  
  
4.  問題が解決されない場合は、\[コンピューターの構成\] ノードの下にある \[管理用テンプレート\]、\[システム\]、\[リモート プロシージャ コール\] と順に開いてから、\[認証されていない RPC クライアントの制限\] グループ ポリシー設定についてドメイン管理者にお問い合わせください。