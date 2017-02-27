---
title: "IDebugBinder::ResolveRuntimeType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::ResolveRuntimeType"
helpviewer_keywords: 
  - "IDebugBinder::ResolveRuntimeType メソッド"
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder::ResolveRuntimeType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはオブジェクトのランタイム型を決定します。  
  
## 構文  
  
```cpp#  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```c#  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### パラメーター  
 `pObject`  
 \[入力\] 解決する [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)。  
  
 `ppResolved`  
 \[入力\] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) としてオブジェクトの型を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 オブジェクトのランタイム型は常にコンパイル時に不明な場合。  たとえばポリモーフィズムを使用すると引数はボタンのクラスなどの基本クラスとして関数に渡すことができます。  実引数はオプション ボタンのクラスなどの派生クラス\) である場合があります。  
  
## 参照  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)