---
title: "IActiveScriptErrorDebug110::GetExceptionThrownKind | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug110::QueryIsFirstChance"
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptErrorDebug110::GetExceptionThrownKind
スローされた例外の種類を示す値を返します。  
  
> [!IMPORTANT]
>  [IActiveScriptErrorDebug110 インターフェイス](../../winscript/reference/iactivescripterrordebug110-interface.md) は、PDM Version 11.0 以降によって実装されます。  activdbg100.h にあります。  
  
## 構文  
  
```  
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### パラメーター  
 `pExceptionKind`  
 \[出力\] [SCRIPT\_ERROR\_DEBUG\_EXCEPTION\_THROWN\_KIND 列挙型](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md) 列挙値で表される、スローされた例外の種類 \(たとえば、初回例外、ハンドルされていない\)。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 参照  
 [IActiveScriptErrorDebug110 インターフェイス](../../winscript/reference/iactivescripterrordebug110-interface.md)