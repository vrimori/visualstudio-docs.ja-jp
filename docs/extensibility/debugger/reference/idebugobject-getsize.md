---
title: "IDebugObject::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetSize"
helpviewer_keywords: 
  - "IDebugObject::GetSize メソッド"
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

バイトのオブジェクトのサイズを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetSize(   
   UINT* pnSize  
);  
```  
  
```c#  
int GetSize(  
   out uint pnSize  
);  
```  
  
#### パラメーター  
 `pnSize`  
 \[入力\] のサイズ \(バイト単位\) を返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 バイト シーケンスとして値を取得するために [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md) のメソッドを使用します。  
  
## 参照  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)