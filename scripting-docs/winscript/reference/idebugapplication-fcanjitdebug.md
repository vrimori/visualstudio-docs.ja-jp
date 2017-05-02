---
title: "IDebugApplication::FCanJitDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FCanJitDebug
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FCanJitDebug"
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FCanJitDebug
Just\-In\-Time \(JIT\) のデバッガーが登録されているかどうかを判定します。  
  
## 構文  
  
```  
BOOL FCanJitDebug();  
```  
  
#### パラメーター  
 このメソッドは、パラメーターを受け取りません。  
  
## 戻り値  
 メソッドが成功し、JIT デバッガーが登録されている場合、メソッドは `TRUE`を返します。  それ以外の場合は、`FALSE` を返します。  
  
## 解説  
 このメソッドは、JIT デバッガーが登録されているかどうかを判定します。  
  
## 参照  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)