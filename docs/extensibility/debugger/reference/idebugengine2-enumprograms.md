---
title: "IDebugEngine2::EnumPrograms | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::EnumPrograms"
helpviewer_keywords: 
  - "IDebugEngine2::EnumPrograms"
ms.assetid: 56bf98eb-beec-4e5f-9ebe-46c922e54c56
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::EnumPrograms
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ エンジン \(DE\) によってデバッグ中のすべてのプログラムの一覧を取得します。  
  
## 構文  
  
```cpp#  
HRESULT EnumPrograms(   
   IEnumDebugPrograms2** ppEnum  
);  
```  
  
```c#  
int EnumPrograms(   
   out IEnumDebugPrograms2 ppEnum  
);  
```  
  
#### パラメーター  
 `ppEnum`  
 \[入力\] de\-DE によってデバッグ中のすべてのプログラムの一覧を含む [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)