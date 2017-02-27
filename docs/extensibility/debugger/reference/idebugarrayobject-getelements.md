---
title: "IDebugArrayObject::GetElements | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetElements"
helpviewer_keywords: 
  - "IDebugArrayObject::GetElements メソッド"
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugArrayObject::GetElements
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

配列のすべての要素の列挙子を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```c#  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### パラメーター  
 `ppEnum`  
 \[入力\] [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) するオブジェクトをすべての要素に列挙できる返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 代わりに要素を反復処理するために [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) と [GetElement](../Topic/IDebugArrayObject::GetElement.md) のメソッドを使用します。  
  
## 参照  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)