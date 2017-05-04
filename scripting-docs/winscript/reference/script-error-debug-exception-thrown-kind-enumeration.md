---
title: "SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 列挙型
スローされた例外の種類を示します。  この列挙型は、[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) メソッドで使用されます。  
  
> [!IMPORTANT]
>  これらの定数は、PDM Version 11.0 以降によって実装されます。  activdbg100.h にあります。  
  
## 構文  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## メンバー  
  
|メンバー|値|説明|  
|----------|-------|--------|  
|ETK\_FIRST\_CHANCE|0x00000000|例外は初回例外です。|  
|ETK\_USER\_UNHANDLED|0x00000001|例外は、ユーザー コードでハンドルされません。|  
|ETK\_UNHANDLED|0x00000002|例外は、コードでハンドルされません。|  
  
## 参照  
 [IActiveScriptErrorDebug110 インターフェイス](../../winscript/reference/iactivescripterrordebug110-interface.md)