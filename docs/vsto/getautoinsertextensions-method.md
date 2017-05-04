---
title: "GetAutoInsertExtensions メソッド | Microsoft Docs"
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
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# GetAutoInsertExtensions メソッド
  自動的にデバッグ中に挿入された Office の apps に関する情報を取得します。  
  
 このメソッドは、今後使用するために予約されています。  
  
## 構文  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### パラメーター  
  
|パラメーター|説明|  
|------------|--------|  
|*psaExtensionNames*|Office の apps の拡張機能の名前。|  
  
## 戻り値  
 メソッドが問題なく完了したかどうかを示す HRESULT 値。  
  
## 解説  
 挿入する Office の各アプリケーションは HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\WEF\\Developer の下の値に対応する Office アプリケーションの拡張機能の名前として返します。  ホストは、レジストリのこれらの値を検索し、次に自動的に拡張機能を挿入する必要があります。  
  
  