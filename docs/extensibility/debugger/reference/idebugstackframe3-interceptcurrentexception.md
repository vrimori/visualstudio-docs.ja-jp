---
title: "IDebugStackFrame3::InterceptCurrentException | Microsoft Docs"
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
  - "IDebugStackFrame3::InterceptCurrentException"
helpviewer_keywords: 
  - "IDebugStackFrame3::InterceptCurrentException"
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

これが現在の例外を受け取るするときに現在のスタック フレームのデバッガーによって呼び出されます。  
  
## 構文  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```c#  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### パラメーター  
 `dwFlags`  
 \[入力\] 異なるアクションを指定します。  現在[INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) の値のみサポートされ`IEA_INTERCEPT` 指定する必要があります。  
  
 `pqwCookie`  
 \[入力\] 特定の例外を識別する一意の値。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
 次は最も一般的なエラーを返します。  
  
|エラー|Description|  
|---------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|現在の例外を受け取ることができません。|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|現在のフレームは実行ハンドラーは検索されません。|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|このメソッドはフレームではサポートされません。|  
  
## 解説  
 例外がスローされると例外処理プロセスの間のキー ポイントの実行時でのデバッガーの実際のコントロール。  これらの主要な時点でデバッガーはフレームが例外を受け取って場合は現在のスタック フレームを呼び出すことができます。  このように傍受された例外はスタック フレームが例外ハンドラー \(たとえばプログラム コードの try\/catch ブロック\) を備えなく場合でも主にスタック フレームの実行時例外ハンドラーです。  
  
 例外は次のような傍受するかどうかをデバッガーがログインすると現在のスタック フレームのオブジェクトのメソッドを呼び出します。  このメソッドは例外の詳細を処理する必要があります。  [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) のインターフェイスが `InterceptStackException` のメソッドはエラー実行されていない場合デバッガーはその例外を処理します。  
  
> [!NOTE]
>  例外がマネージ コードでのみデバッグ対象が .NET ランタイムで実行されている場合つまり受け取ることができます。  またサードパーティの言語では選択した独自のデバッグ エンジンの `InterceptStackException` を実行できます。  
  
 傍受が完了したら[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) はシグナル。  
  
## 参照  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)