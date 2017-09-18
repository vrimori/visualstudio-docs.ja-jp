---
title: "IDebugProgramEngines2::SetEngine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEngines2::SetEngine"
helpviewer_keywords: 
  - "IDebugProgramEngines2::SetEngine"
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramEngines2::SetEngine
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプログラムをデバッグに使用するデバッグ エンジンをプログラム \(DE\) またはプログラムのノードを示しています。  
  
## 構文  
  
```cpp#  
HRESULT SetEngine(   
   REFGUID guidEngine  
);  
```  
  
```c#  
int SetEngine(   
   ref Guid guidEngine  
);  
```  
  
#### パラメーター  
 `guidEngine`  
 \[入力\] GUID します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)