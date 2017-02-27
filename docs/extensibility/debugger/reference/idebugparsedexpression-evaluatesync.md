---
title: "IDebugParsedExpression::EvaluateSync | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugParsedExpression::EvaluateSync"
helpviewer_keywords: 
  - "IDebugParsedExpression::EvaluateSync メソッド"
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugParsedExpression::EvaluateSync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドは解析された式を評価し別のデータ型の結果ができます。  
  
## 構文  
  
```cpp#  
HRESULT EvaluateSync(   
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BSTR                  bstrResultType,  
   IDebugProperty2**     ppResult  
);  
```  
  
```c#  
int EvaluateSync(  
   uint                 dwEvalFlags,   
   uint                 dwTimeout,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   string               bstrResultType,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### パラメーター  
 `dwEvalFlags`  
 \[入力\] 式の評価方法を制御する [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) の定数の組み合わせ。  
  
 `dwTimeout`  
 \[出力\] このメソッドから制御が戻るまで待機するミリ秒単位の最大時間を指定します。  無期限に待機するために `INFINITE` を使用します。  
  
 `pSymbolProvider`  
 \[入力\] [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) インターフェイスとして表現されたシンボルのプロバイダー。  
  
 `pAddress`  
 \[入力\] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) インターフェイスとして表現されるメソッド内の現在の実行場所。  
  
 `pBinder`  
 \[入力\] [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) インターフェイスとして表現されるバインダー。  
  
 `bstrResultType`  
 \[出力\] 型は結果にキャストする必要があります。  この引数は null になることがあります。  
  
 `ppResult`  
 \[入力\] 評価の結果を表す [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) のインターフェイスを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 含むメソッドを特定し式のシンボル値を決定する言語のスコープ規則を使用できる式の評価は `pAddress` のコンテキストで指定します。  
  
## 参照  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)