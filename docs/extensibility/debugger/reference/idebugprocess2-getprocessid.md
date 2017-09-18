---
title: "IDebugProcess2::GetProcessId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetProcessId"
helpviewer_keywords: 
  - "IDebugProcess2::GetProcessId"
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::GetProcessId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプロセスの GUID を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetProcessId(  
   GUID* pguidProcessId  
);  
```  
  
```c#  
int GetProcessId(  
   out Guid pguidProcessId  
);  
```  
  
#### パラメーター  
 `pguidProcessId`  
 \[出力\] このプロセスの GUID を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 グローバル一意識別子は \(GUID\)システム上の他のすべての実行中のプロセスからこのプロセスを識別します。  
  
## 参照  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)