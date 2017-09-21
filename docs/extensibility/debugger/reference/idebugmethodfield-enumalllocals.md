---
title: "IDebugMethodField::EnumAllLocals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumAllLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumAllLocals メソッド"
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

コンパイラによって内部的に生成されたものも含めてすべてのメソッドのローカル変数の列挙子を作成します。  
  
## 構文  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### パラメーター  
 `pAddress`  
 \[入力\] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) に特定のスコープまたはコンテキスト内にメソッドのデバッグのアドレスをポイントします。  
  
 `ppLocals`  
 \[入力\] [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) を表すオブジェクトを指定されたスコープ内のすべてのローカルのリストを返します ; それ以外の場合はローカルを示さない場合は NULL。  
  
## 戻り値  
 S\_FALSEは S\_OK または成功している場合を返します。  それ以外の場合はエラー コード。  
  
## 解説  
 特定のデバッグのアドレスを含むブロック内で定義されている変数のみを列挙します。  このメソッドはコンパイラが生成したローカルが含まれます。  必要なソースで明示的に定義されているすべてのローカル [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) のメソッドを呼び出します。  
  
 メソッドのコンテキストまたはスコープは複数のブロックを含めることができます。  
  
## 参照  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)