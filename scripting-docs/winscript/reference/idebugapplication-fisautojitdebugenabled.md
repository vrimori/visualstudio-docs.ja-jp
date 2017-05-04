---
title: "IDebugApplication::FIsAutoJitDebugEnabled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FIsAutoJitDebugEnabled
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FIsAutoJitDebugEnabled"
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FIsAutoJitDebugEnabled
Just\-In\-Time \(JIT\) のデバッガーを自動登録済みのデバッグ中の言えないホストであるかどうかを判定します。  
  
## 構文  
  
```  
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### パラメーター  
 このメソッドは、パラメーターを受け取りません。  
  
## 戻り値  
 メソッドが成功し、JIT デバッガーが自動登録済みのデバッグ中の言えないホストの場合、メソッドは `TRUE`を返します。  それ以外の場合は、`FALSE` を返します。  
  
## 解説  
 このメソッドは、JIT デバッガーが自動登録済みのデバッグ中の言えないホストであるかどうかを判定します。  
  
## 参照  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)