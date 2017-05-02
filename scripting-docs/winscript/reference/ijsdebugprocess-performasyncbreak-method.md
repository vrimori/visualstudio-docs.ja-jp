---
title: "IJsDebugProcess::PerformAsyncBreak メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.PerformAsyncBreak
apilocation: jscript9diag.dll
ms.assetid: 2a6ee369-ea99-4332-8521-a1741ccb6292
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugProcess::PerformAsyncBreak メソッド
スクリプト エンジンを中断モードにして、次のスクリプト命令で中断させます。  
  
## 構文  
  
```  
HRESULT PerformAsyncBreak(  
   DWORD threadId  
);  
```  
  
#### パラメーター  
 `threadId`  
 \[入力\] スレッドの ID。  
  
## 戻り値  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugProcess インターフェイス](../../winscript/reference/ijsdebugprocess-interface.md)