---
title: "IEnumDebugPrograms2::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPrograms2::Reset"
helpviewer_keywords: 
  - "IEnumDebugPrograms2::Reset"
ms.assetid: b289242b-24ea-4df3-a811-20b0c8a903d6
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPrograms2::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

最初の要素には列挙型をリセットします。  
  
## 構文  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```c#  
int Reset();  
```  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドが呼び出された後[次へ](../Topic/IEnumDebugPrograms2::Next.md) のメソッドの回復列挙型の最初の要素。  
  
## 参照  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)