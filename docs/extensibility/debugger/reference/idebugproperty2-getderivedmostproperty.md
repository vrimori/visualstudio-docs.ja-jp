---
title: "IDebugProperty2::GetDerivedMostProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
helpviewer_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::GetDerivedMostProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プロパティの取得プロパティを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```c#  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### パラメーター  
 `ppDerivedMost`  
 \[入力\] 取得するプロパティを表す [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  取得するプロパティが存在しない場合派生 `S_GETDERIVEDMOST_NO_DERIVED_MOST` を返します。  
  
## 解説  
 たとえばプロパティが実際に `ClassRoot` から派生した `ClassDerived` のインスタンス化であるオブジェクトを実装する `ClassRoot` 記述する場合はこのメソッドは `ClassDerived` のオブジェクトを表す [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) のオブジェクト。  
  
## 参照  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)