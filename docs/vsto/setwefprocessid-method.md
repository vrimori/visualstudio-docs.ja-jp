---
title: "SetWefProcessId メソッド"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# SetWefProcessId メソッド
  Web 拡張機能の Framework \(WEF\) のコンテンツを実行するプロセス識別子を指定します。  
  
## 構文  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### パラメーター  
  
|パラメーター|説明|  
|------------|--------|  
|*dwProcessId*|WEF のコンテンツを実行するプロセス識別子。|  
  
## 戻り値  
 メソッドが問題なく完了したかどうかを示す HRESULT 値。  
  
## 解説  
 このメソッドは WEF の内容のプロセスが作成された後、WEF のコンテンツが実行される前に呼び出す必要があります。  
  
 開発環境に WEF の内容のプロセスにデバッガーをアタッチする場合、環境は、このメソッドの実装でこの操作を実行する必要があります。  
  
  