---
title: "IDebugCookie::SetDebugCookie | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCookie.SetDebugCookie
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugCookie::SetDebugCookie"
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCookie::SetDebugCookie
デバッグのアプリケーションのクッキーを設定します。  
  
## 構文  
  
```  
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### パラメーター  
 `dwDebugAppCookie`  
 \[入力\]デバッグ アプリケーションを識別する、クッキー。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、いくつかのデバッガーをプロセスにアタッチしながら、デバッグ アプリケーションのクッキーを設定します。  
  
## 参照  
 [IDebugCookie インターフェイス](../../winscript/reference/idebugcookie-interface.md)