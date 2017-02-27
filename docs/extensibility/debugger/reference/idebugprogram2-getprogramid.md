---
title: "IDebugProgram2::GetProgramId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetProgramId"
helpviewer_keywords: 
  - "IDebugProgram2::GetProgramId"
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::GetProgramId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプログラムの GUID を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```c#  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### パラメーター  
 `pguidProgramId`  
 \[出力\] このプログラムの `GUID` を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 デバッグ エンジンは \(DE\)最初に [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) または [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) のメソッドに渡されるプログラム ID を返す必要があります。  これにはデバッガー コンポーネント間でプログラムを識別できます。  
  
## 参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)