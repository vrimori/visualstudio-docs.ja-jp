---
title: "IDebugStackFrame3::InterceptCurrentException |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9842527f90d9b2df7308f1e80e337de2848d9179
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
現在の例外をインターセプトする必要がある場合に、現在のスタック フレーム上でデバッガーによって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFlags`  
 [in]さまざまな操作を指定します。 現時点では、のみ、 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)値`IEA_INTERCEPT`はサポートされており、指定する必要があります。  
  
 `pqwCookie`  
 [out]特定の例外を識別する一意の値です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
 次に、最も一般的なエラーを返します。  
  
|Error|説明|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|現在の例外を受け取ることができません。|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|実行の現在のフレームをまだハンドラーの検索されていません。|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|このメソッドはこのフレームのサポートされていません。|  
  
## <a name="remarks"></a>コメント  
 例外がスローされると、デバッガーは、例外がプロセスを処理中に主要なポイントで実行時からコントロールを取得します。 こうしたキー瞬間中に、デバッガーは、特定のフレームが例外をインターセプトするか、現在のスタック フレームを依頼できます。 この方法では、傍受した例外は、そのスタック フレームは、例外ハンドラー (たとえば、プログラム コードでの try/catch ブロック) を持っていない場合でもスタック フレームの場での例外ハンドラー本質的です。  
  
 デバッガーが例外を受け取るかどうかを把握したい場合に、現在のスタック フレーム オブジェクトに対してこのメソッドを呼び出します。 このメソッドは、例外の詳細をすべての処理を担当します。 場合、 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)インターフェイスが実装されていません、または`InterceptStackException`メソッドには、エラーが返されますし、デバッガーは、通常、例外の処理を続行します。  
  
> [!NOTE]
>  例外をインターセプトできます、マネージ コードでのみ、デバッグ中のプログラムは .NET ランタイムで実行する場合。 もちろん、サード パーティ製言語実装者を実装できます`InterceptStackException`のように選択する場合、独自のデバッグ エンジンです。  
  
 傍受が完了した後、 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)がシグナルを受け取る。  
  
## <a name="see-also"></a>参照  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)