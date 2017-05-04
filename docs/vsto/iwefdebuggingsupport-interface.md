---
title: "IWefDebuggingSupport インターフェイス | Microsoft Docs"
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
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# IWefDebuggingSupport インターフェイス
  Office の apps のデバッグを簡単にするために、Visual Studio などのデバッグ環境で実行されます。  Office アプリケーションは、Word や Excel など、Visual Studio からこのインターフェイスを取得し、次にある時点でのデバッグ セッション中にインターフェイスのメソッドを呼び出します。  
  
## 構文  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## メソッド  
 次の表は IWefDebuggingSupport のインターフェイスが定義するメソッドの一覧を示します。  
  
|名前|説明|  
|--------|--------|  
|[GetAutoInsertExtensions メソッド](../vsto/getautoinsertextensions-method.md)|自動的にデバッグ中に挿入された Office の apps に関する情報を取得します。|  
|[SetWefProcessId メソッド](../vsto/setwefprocessid-method.md)|Web 拡張機能の Framework \(WEF\) のコンテンツを実行するプロセス識別子を指定します。|  
  
  