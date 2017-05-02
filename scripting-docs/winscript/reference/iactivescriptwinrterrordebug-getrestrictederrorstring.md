---
title: "IActiveScriptWinRTErrorDebug::GetRestrictedErrorString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug::GetRestrictedErrorString"
ms.assetid: d901e049-fb1b-4101-a04a-1395d657f1cf
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
Windows のランタイムによって制限されるエラー文字列を、可能であれば返します。  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug インターフェイス](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) は PDM v11.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## 構文  
  
```cpp  
HRESULT GetRestrictedErrorString([out] BSTR * errorString);  
  
```  
  
#### パラメーター  
 `errorString`  
 \[入力\]エラー制限された文字列。  
  
## 参照  
 [IActiveScriptWinRTErrorDebug インターフェイス](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)