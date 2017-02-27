---
title: "IDebugFunctionObject::CreateArrayObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateArrayObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateArrayObject メソッド"
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

配列オブジェクトを作成します。  この配列はプリミティブ型またはオブジェクト インスタンスの値を含むことができます。  
  
## 構文  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### パラメーター  
 `ot`  
 \[入力\] 新しい配列オブジェクトの種類を示す [OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md) の列挙値を指定します。  
  
 `pClassField`  
 \[入力\] オブジェクト インスタンスで配列を作成するときは[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) を表すオブジェクトのクラス。  基本的なオブジェクトの配列を作成する場合はこのパラメーターは null 値です。  
  
 `dwRank`  
 \[入力\] 配列のランクまたは次元の数。  
  
 `dwDims`  
 \[入力\] 配列の各次元のサイズ。  
  
 `dwLowBounds`  
 \[入力\] 各次元の原点 \(通常は 0 か 1\)。  
  
 `ppObject`  
 \[入力\] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) に新しく作成された配列を返します。  これは実際に [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) のオブジェクトです。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) のインターフェイスで表される関数への配列パラメーターを表すオブジェクトを作成するためにこのメソッドを呼び出します。  
  
## 参照  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)