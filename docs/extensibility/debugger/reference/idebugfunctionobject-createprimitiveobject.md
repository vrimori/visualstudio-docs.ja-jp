---
title: "IDebugFunctionObject::CreatePrimitiveObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreatePrimitiveObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreatePrimitiveObject メソッド"
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugFunctionObject::CreatePrimitiveObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

単純な整数などの基本データ オブジェクトを作成します。  
  
## 構文  
  
```cpp#  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### パラメーター  
 `ot`  
 \[入力\] 作成するにはプリミティブの型を表す [OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md) の列挙体の値。  
  
 `ppObject`  
 \[出力\] 新しく作成されたオブジェクトを表す [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) を返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) のインターフェイスで表される関数にパラメーターがある基本オブジェクトを表すオブジェクトを作成するためにこのメソッドを呼び出します。  たとえば正規表現文字列が 「表すオブジェクトを作成するために myString \(5\) 」の場合このメソッドは整数 5. 使用されます。  
  
## 参照  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)