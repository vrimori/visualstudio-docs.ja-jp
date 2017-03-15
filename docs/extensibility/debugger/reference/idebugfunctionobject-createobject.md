---
title: "IDebugFunctionObject::CreateObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateObject メソッド"
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

コンストラクターを使用してオブジェクトを作成します。  
  
## 構文  
  
```cpp#  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### パラメーター  
 `pConstructor`  
 \[入力\] [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) に作成するオブジェクトのコンストラクター。  
  
 `dwArgs`  
 \[入力\]`pArg` の配列パラメーターの数。  コンストラクターに渡されるパラメーターの数を表します。  
  
 `pArg`  
 \[入力\] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) を表すオブジェクトの配列コンストラクターに渡されるパラメーター。  
  
 `ppObject`  
 \[出力\] 新しく作成されたオブジェクトを表す `IDebugObject` を返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 クラスを表すオブジェクトを作成するためにこのメソッドを呼び出します \(またはパラメーターが [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) のインターフェイスで表される関数になるコンストラクターを必要とする他の複合型のインスタンスを示します。  
  
 オブジェクトはコンストラクターのパラメーターが必要な場合は[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) のメソッドを呼び出します。  
  
## 参照  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)