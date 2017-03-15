---
title: "IDebugProgramNodeAttach2::OnAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
helpviewer_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 3
---
# IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

関連するプログラムまたは延期にアタッチしたり [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) のメソッドにアタッチするプロセス。  
  
## 構文  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```c#  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### パラメーター  
 `guidProgramId`  
 \[入力\] 関連するプログラムに割り当てる `GUID`。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) のメソッドを呼び出すと `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドはプロセス中に [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) のメソッドを呼び出す前に呼び出します。  `OnAttach` のメソッドはプロセス自体をこのメソッドは `S_FALSE` 実行\) または `IDebugEngine2::Attach` のメソッド \(`OnAttach` のメソッド `S_OK`\) のプロセスにアタッチを行うこともできます。  いずれの場合も`OnAttach` のメソッドは特定の `GUID` にデバッグするプログラムの `GUID` を設定できます。  
  
## 参照  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)