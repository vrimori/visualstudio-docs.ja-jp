---
title: "IDebugExpression2::EvaluateSync | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2::EvaluateSync"
helpviewer_keywords: 
  - "IDebugExpression2::EvaluateSync"
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugExpression2::EvaluateSync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドは式を同期的に評価されます。  
  
## 構文  
  
```cpp#  
HRESULT EvaluateSync(   
   EVALFLAGS             dwFlags,  
   DWORD                 dwTimeout,  
   IDebugEventCallback2* pExprCallback,  
   IDebugProperty2**     ppResult  
);  
```  
  
```c#  
int EvaluateSync(  
   enum_EVALFLAGS       dwFlags,   
   uint                 dwTimeout,   
   IDebugEventCallback2 pExprCallback,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### パラメーター  
 `dwFlags`  
 \[入力\] 式の評価を制御する [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) の列挙体のフラグの組み合わせ。  
  
 `dwTimeout`  
 \[出力\] このメソッドから制御が戻るまで待機する最大時間 \(ミリ秒単位\)。  無期限に待機するために `INFINITE` を使用します。  
  
 `pExprCallback`  
 \[入力\] このパラメーターは null 値は常にです。  
  
 `ppResult`  
 \[入力\] 式の評価の結果を含む [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  一般的なエラー コードは次のとおりです :  
  
|エラー|Description|  
|---------|-----------------|  
|E\_EVALUATE\_BUSY\_WITH\_EVALUATION|別の式は現在同時に評価される式の評価はサポートされません。|  
|E\_EVALUATE\_TIMEOUT|評価がタイムアウトした場合。|  
  
## 解説  
 同期の評価は評価が完了するとVisual Studio にイベントを戻す必要はありません。  
  
## 使用例  
 次の例に `CExpression` の単純なオブジェクトに対してこのメソッドを実装する方法を実装するインターフェイスの [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) 示します。  
  
```cpp#  
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,  
                                  DWORD dwTimeout,  
                                  IDebugEventCallback2* pExprCallback,  
                                  IDebugProperty2** ppResult)  
{  
    // Set the aborted state to FALSE.    
    m_bAborted = FALSE;    
    // Delegate the evaluation to EvalExpression.    
    return EvalExpression(TRUE, ppResult);    
}  
  
HRESULT CExpression::EvalExpression(BOOL bSynchronous,  
                                    IDebugProperty2** ppResult)  
{  
    HRESULT hr;  
  
    // Get the value of an environment variable.  
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);  
    // Create and initialize a CEnvVar object with the retrieved value.  
    // CEnvVar implements the IDebugProperty2 interface.  
    CComObject<CEnvVar> *pEnvVar;  
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);  
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);  
  
    if (pszVal) {  
        // Check for synchronous evaluation.  
        if (bSynchronous) {  
            // Set and AddRef the result, IDebugProperty2 interface.  
            *ppResult = pEnvVar;  
            (*ppResult)->AddRef();  
            hr = S_OK;  
        } else {  
            //For asynchronous evaluation, send an evaluation complete event.  
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);  
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);  
        }  
    } else {  
        // If a valid value is not retrieved, return E_FAIL.  
        hr = E_FAIL;  
    }  
    return hr;  
}  
```  
  
## 参照  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)