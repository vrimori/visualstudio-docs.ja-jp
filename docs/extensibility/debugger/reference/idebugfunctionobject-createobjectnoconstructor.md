---
title: "IDebugFunctionObject::CreateObjectNoConstructor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateObjectNoConstructor"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateObjectNoConstructor メソッド"
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::CreateObjectNoConstructor
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

コンストラクターを持たないオブジェクトを作成します。  
  
## 構文  
  
```cpp#  
HRESULT CreateObjectNoConstructor(   
   IDebugField*   pClassObject,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateObjectNoConstructor(  
   IDebugField      pClassField,   
   out IDebugObject ppObject  
);  
```  
  
#### パラメーター  
 `pClassObject`  
 \[入力\] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) に作成されるオブジェクトの型。  
  
 `ppObject`  
 \[出力\] 新しく作成されたオブジェクトを表す [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) を返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 パラメーターは [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) のインターフェイスで表される関数であること \(コンストラクターを必要としない構造体または複合型\) のインスタンスを表すオブジェクトを作成するためにこのメソッドを呼び出します。  
  
 オブジェクトはコンストラクターのパラメーターが必要な場合は[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) のメソッドを呼び出します。  
  
## 参照  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)