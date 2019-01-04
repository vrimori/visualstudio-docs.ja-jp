---
title: IDebugExpressionContext2::ParseText |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4178520b1d51e57a302c817c6c97a10c640aa6fe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945419"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
以降の評価のためのテキスト形式の式を解析します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ParseText(   
   LPCOLESTR           pszCode,  
   PARSEFLAGS          dwFlags,  
   UINT                nRadix,  
   IDebugExpression2** ppExpr,  
   BSTR*               pbstrError,  
   UINT*               pichError  
);  
```  
  
```csharp  
int ParseText(   
   string                pszCode,  
   enum_PARSEFLAGS       dwFlags,  
   uint                  nRadix,  
   out IDebugExpression2 ppExpr,  
   out string            pbstrError,  
   out uint              pichError  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszCode`  
 [in]解析する式。  
  
 `dwFlags`  
 [in]フラグの組み合わせ、 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)解析を制御する列挙体。  
  
 `nRadix`  
 [in]内の数値情報を解析中に使用する基数`pszCode`します。  
  
 `ppExpr`  
 [out]返します、 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)バインドと評価の準備ができて、解析された式を表すオブジェクト。  
  
 `pbstrError`  
 [out]式にエラーが含まれている場合は、エラー メッセージを返します。  
  
 `pichError`  
 [out]内のエラーの文字インデックスを返します`pszCode`式にエラーが含まれている場合。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドが呼び出されると、デバッグ エンジン (DE) が式を解析およびが正しいかどうかを検証する必要があります。 `pbstrError`と`pichError`式が有効でない場合パラメーターを入力する場合があります。  
  
 ある式は評価されず、解析のみに注意してください。 以降の呼び出し、 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)または[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)メソッドが解析された式を評価します。  
  
## <a name="example"></a>例  
 次の例は、単純なは、このメソッドを実装する方法を示しています。`CEnvBlock`を公開するオブジェクト、 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイス。 この例では、環境変数の名前として解析される式を考慮し、その変数の値を取得します。  
  
```cpp  
HRESULT CEnvBlock::ParseText(  
   LPCOLESTR           pszCode,  
   PARSEFLAGS          dwFlags,  
   UINT                nRadix,  
   IDebugExpression2 **ppExpr,  
   BSTR               *pbstrError,  
   UINT               *pichError)  
{  
   HRESULT hr = E_OUTOFMEMORY;    
   // Create an integer variable with a value equal to one plus    
   // twice the length of the passed expression to be parsed.    
   int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;    
   // Allocate a character string of the same length.    
   char *pszAnsiCode = (char *) malloc(iAnsiLen);    
  
   // Check for successful memory allocation.    
   if (pszAnsiCode) {    
      // Map the wide-character pszCode string to the new pszAnsiCode character string.    
      WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);    
      // Check to see if the app can succesfully get the environment variable.    
      if (GetEnv(pszAnsiCode)) {    
  
         // Create and initialize a CExpression object.    
         CComObject<CExpression> *pExpr;    
         CComObject<CExpression>::CreateInstance(&pExpr);    
            pExpr->Init(pszAnsiCode, this, NULL);    
  
         // Assign the pointer to the new object to the passed argument  
         // and AddRef the object.    
         *ppExpr = pExpr;    
         (*ppExpr)->AddRef();    
         hr = S_OK;    
      // If the program cannot succesfully get the environment variable.    
      } else {    
         // Set the errror message and return E_FAIL.    
         *pbstrError = SysAllocString(L"No such environment variable.");    
         hr = E_FAIL;    
      }    
      // Free the local character string.    
      free(pszAnsiCode);    
   }    
   return hr;    
}    
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)