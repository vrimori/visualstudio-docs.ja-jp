---
title: "IDebugSyncOperation::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.Execute
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::Execute"
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::Execute
同期的に処理し、を返します。  
  
## 構文  
  
```  
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### パラメーター  
 `ppunkResult`  
 \[入力\]オブジェクトのパラメーターは、操作によって返される。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_ABORT`|操作は `IDebugSyncOperation::InProgressAbort` のメソッドを呼び出して、中止されます。|  
  
## 解説  
 対象のスレッドのプロセス デバッグ マネージャーは `Execute` のメソッドを同期的に呼び出します。  
  
## 参照  
 [IDebugSyncOperation インターフェイス](../../winscript/reference/idebugsyncoperation-interface.md)