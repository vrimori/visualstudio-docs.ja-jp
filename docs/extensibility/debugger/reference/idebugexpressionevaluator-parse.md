---
title: "IDebugExpressionEvaluator::Parse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::Parse"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::Parse メソッド"
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExpressionEvaluator::Parse
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドは解析された式の式は文字列をに変換します。  
  
## 構文  
  
```cpp#  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```c#  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### パラメーター  
 `upstrExpression`  
 \[入力\] 解析する文字列式。  
  
 `dwFlags`  
 \[入力\] 式を解析する方法を決定 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) の定数のコレクション。  
  
 `nRadix`  
 \[入力\] 数値情報を解釈するために使用する基数。  
  
 `pbstrError`  
 \[入力\] 人間が判読できるテキストとしてエラーを返します。  
  
 `pichError`  
 \[入力\] エラーの文字列式の文字位置を返します。  
  
 `ppParsedExpression`  
 \[入力\] [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) のオブジェクトの解析された式を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドは解析された式の値ではなくを生成します。  解析された式を計算する準備が整いました。つまり値に変換します。  
  
## 参照  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)