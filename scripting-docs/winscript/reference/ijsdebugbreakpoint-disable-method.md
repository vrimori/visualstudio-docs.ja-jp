---
title: "IJsDebugBreakPoint::Disable メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.Disable
apilocation: jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugBreakPoint::Disable メソッド
Disables the breakpoint.  
  
## 構文  
  
```  
HRESULT Disable(void);  
```  
  
## 戻り値  
  
## 解説  
 Returns E\_UNEXPECTED if called on a deleted breakpoint.  既に無効になっているブレークポイントで呼び出された場合は S\_FALSE を返します。  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugBreakPoint インターフェイス](../../winscript/reference/ijsdebugbreakpoint-interface.md)