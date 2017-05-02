---
title: "IJsDebugDataTarget::GetThreadContext メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetThreadContext
apilocation: jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::GetThreadContext メソッド
Retrieves context for given thread.  
  
## 構文  
  
```  
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### パラメーター  
 `threadId`  
 \[in\] Thread running in the target process.  
  
 `contextFlags`  
 \[入力\] コンテキスト フラグを指定します。  これは CONTEXT の ContextFlags フィールドと同じです \(詳細については「winnt.h」で「CONTEXT\_ALL」を参照\)。  
  
 `contextSize`  
 \[入力\] pContext で指定したバッファーのサイズ。  
  
 `pContext`  
 \[出力\] pContext で指定したバッファーでプラットフォーム固有の CONTEXT 構造体を受け取ります。  
  
## 戻り値  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)