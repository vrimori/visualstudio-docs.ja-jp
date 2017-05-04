---
title: "IJsDebugBreakPoint::IsEnabled メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.IsEnabled
apilocation: jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugBreakPoint::IsEnabled メソッド
ブレークポイントが有効かどうかを指定します。  
  
## 構文  
  
```  
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### パラメーター  
 `pIsEnabled`  
 \[出力\] ブレークポイントが有効な場合は true を、それ以外の場合は false を返します。  
  
## 戻り値  
  
## 解説  
 削除されたブレークポイントで呼び出された場合は E\_UNEXPECTED を返します。  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugBreakPoint インターフェイス](../../winscript/reference/ijsdebugbreakpoint-interface.md)