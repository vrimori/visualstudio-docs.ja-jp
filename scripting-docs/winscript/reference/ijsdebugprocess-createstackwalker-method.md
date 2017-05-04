---
title: "IJsDebugProcess::CreateStackWalker メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateStackWalker
apilocation: jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugProcess::CreateStackWalker メソッド
スタック ウォーカーのファクトリ メソッド。  
  
## 構文  
  
```  
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### パラメーター  
 `threadId`  
 \[in\] The thread ID.  
  
 `ppStackWalker`  
 \[出力\] 新しいスタック ウォーカー オブジェクト。  
  
## 戻り値  
  
## 解説  
 スレッドに JavaScript がない場合は E\_JsDEBUG\_UNKNOWN\_THREAD を返します。  ターゲット プロセスの停止中にのみ、このメソッドを呼び出すことができます。  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugProcess インターフェイス](../../winscript/reference/ijsdebugprocess-interface.md)