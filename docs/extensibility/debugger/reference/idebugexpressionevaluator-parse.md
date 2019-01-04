---
title: IDebugExpressionEvaluator::Parse |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebd8518a6fd2048de0d5204dcede8943f4da62e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922195"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
このメソッドは、式の文字列を解析された式に変換します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `upstrExpression`  
 [in]解析対象の式の文字列。  
  
 `dwFlags`  
 [in]コレクション[PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)式の解析方法を決定する定数。  
  
 `nRadix`  
 [in]任意の数値情報を解釈するための基数。  
  
 `pbstrError`  
 [out]人間が判読できるテキストとして、エラーを返します。  
  
 `pichError`  
 [out]式の文字列で、エラーの開始文字位置を返します。  
  
 `ppParsedExpression`  
 [out]解析された式を返します、 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、実際の値ではなく、解析された式を生成します。 解析された式は、値に変換は、すぐに評価できますします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)