---
title: "IDebugFunctionObject::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::Evaluate"
helpviewer_keywords: 
  - "IDebugFunctionObject::Evaluate メソッド"
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

関数を呼び出してオブジェクトとして結果値を返します。  
  
## 構文  
  
```cpp#  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### パラメーター  
 `ppParams`  
 \[入力\] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) の入力パラメーターを表すオブジェクトの配列。  これらのパラメーターは [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) のインターフェイスのメソッドの `Create` 1 で作成されています。  
  
 `dwParams`  
 \[入力\] `ppParams` の配列パラメーターの数。  
  
 `dwTimeout`  
 \[出力\] このメソッドから制御が戻るまで待機するミリ秒単位の最大時間を指定します。  無期限に待機するために `INFINITE` を使用します。  
  
 `ppResult`  
 \[入力\] オブジェクトとして関数値を表す [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) を返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドは [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) のオブジェクトによって表される関数への呼び出しを設定し実行します。  
  
## 参照  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)