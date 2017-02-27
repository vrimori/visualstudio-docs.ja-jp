---
title: "IDebugProcess2::EnumPrograms | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::EnumPrograms"
helpviewer_keywords: 
  - "IDebugProcess2::EnumPrograms"
ms.assetid: f5b7295d-487d-464f-a4c6-d54175b07705
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::EnumPrograms
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプロセスに含まれるすべてのプログラムの一覧を取得します。  
  
## 構文  
  
```cpp#  
HRESULT EnumPrograms(   
   IEnumDebugPrograms2** ppEnum  
);  
```  
  
```c#  
int EnumPrograms(   
   out IEnumDebugPrograms2 ppEnum  
);  
```  
  
#### パラメーター  
 `ppEnum`  
 \[出力\] プロセス内ですべてのプログラムの一覧を含む [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)