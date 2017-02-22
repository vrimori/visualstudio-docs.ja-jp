---
title: "IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::GetMethodProperty"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::GetMethodProperty メソッド"
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはメソッドにローカル引数およびそのほかのプロパティを含むプロパティ オブジェクトを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```c#  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### パラメーター  
 `pSymbolProvider`  
 \[入力\] 使用されるシンボルのプロバイダー [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) のオブジェクトとして表現されます。  
  
 `pAddress`  
 \[入力\] 最も近い含む関数に解決される [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) のオブジェクトとして表現されるコードのアドレス。  
  
 `pBinder`  
 \[入力\] 使用されるバインダー [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) のオブジェクトとして表現されます。  
  
 `fIncludeHiddenLocals`  
 \[入力\] 非表示になっているローカル変数の格納 `TRUE`\(\) 以外の手段 ; 非表示になっているローカルを保持 `FALSE`\(ゼロ\)。  
  
 `ppProperty`  
 \[入力\] [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) のメソッドを表すオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 非表示のローカルはコンパイラによって生成された変数です。  
  
## 参照  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)