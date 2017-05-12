---
title: "IDebugApplication::CreateAsyncDebugOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.CreateAsyncDebugOperation
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::CreateAsyncDebugOperation"
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::CreateAsyncDebugOperation
特定の同期デバッグの非同期操作へのアクセスを提供します。  
  
## 構文  
  
```  
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### パラメーター  
 `psdo`  
 \[入力\]デバッグ操作の同期オブジェクト。  
  
 `ppado`  
 \[入力\]デバッグ非同期操作のオブジェクト。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、言語のエンジンがデバッガーのスレッドに明示的に同期で式を非同期的に評価するようにします。  詳細については、「[IDebugSyncOperation インターフェイス](../../winscript/reference/idebugsyncoperation-interface.md)」および「[IDebugAsyncOperation インターフェイス](../../winscript/reference/idebugasyncoperation-interface.md)」を参照してください。  
  
## 参照  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugSyncOperation インターフェイス](../../winscript/reference/idebugsyncoperation-interface.md)   
 [IDebugAsyncOperation インターフェイス](../../winscript/reference/idebugasyncoperation-interface.md)