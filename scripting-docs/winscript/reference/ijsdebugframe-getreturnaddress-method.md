---
title: "IJsDebugFrame::GetReturnAddress メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetReturnAddress
apilocation: jscript9diag.dll
ms.assetid: 7f10c1d6-d7b9-402e-9020-04cded37f9d3
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetReturnAddress メソッド
Gets the return address pushed at the 'start' \(see GetStackRange\) of the frame.  
  
## 構文  
  
```  
HRESULT GetReturnAddress(  
   UINT64 *pReturnAddress  
);  
```  
  
#### パラメーター  
 `pReturnAddress`  
 \[出力\] リターン アドレス。  
  
## 戻り値  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugFrame インターフェイス](../../winscript/reference/ijsdebugframe-interface.md)