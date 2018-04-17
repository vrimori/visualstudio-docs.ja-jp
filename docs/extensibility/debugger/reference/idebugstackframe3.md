---
title: IDebugStackFrame3 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 635b53bf63eb83cc868e4bf9b7d5fbb31fe5aa08
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
このインターフェイスを拡張[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)傍受した例外を処理します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) を実装する同一のオブジェクトにこのインターフェイスを実装する、 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)傍受した例外をサポートするインターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、`IDebugStackFrame2`インターフェイスをこのインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 継承されたメソッドだけでなく[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)、`IDebugStackFrame3`は次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|任意の通常の例外処理の前に、現在のスタック フレームの例外を処理します。|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|スタック アンワインドが発生した場合は、コードのコンテキストを返します。|  
  
## <a name="remarks"></a>コメント  
 傍受した例外は、通常の例外処理ルーチンは、ランタイムによって呼び出される前に、デバッガーが例外を処理できることを意味します。 例外をインターセプトし、基本的には、実行時間がある例外ハンドラーがない場合にも存在として扱わを行うを意味します。  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)標準の例外のすべてのコールバック イベント中に呼び出されます (唯一の例外がのかどうかはコードをデバッグする混合モード (マネージし、アンマネージ コード)、中に例外をインターセプトできない場合、最終コールバック)。 デを実装しない場合`IDebugStackFrame3`、か、DE IDebugStackFrame3 からエラーが返されます::`InterceptCurrentException` (など`E_NOTIMPL`)、デバッガーが通常は、例外を処理し、します。  
  
 例外をインターセプトし、によって、デバッガーはデバッグ中のプログラムの状態を変更して、例外がスローされた時点での実行を再開するユーザーを許可できます。  
  
> [!NOTE]
>  傍受した例外は、共通言語ランタイム (CLR) 下で実行しているプログラムでは、マネージ コードでのみ許可されてです。  
  
 デバッグ エンジンを示す"metricExceptions"を設定して、受信の例外をサポートしている値の 1 に実行時に使用して、`SetMetric`関数。 詳細については、次を参照してください。[をデバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)