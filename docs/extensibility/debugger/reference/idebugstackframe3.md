---
title: IDebugStackFrame3 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 376807a2963e93b3713d85b2d166c741671079bf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932773"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
このインターフェイスは拡張[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)傍受した例外を処理します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) を実装する同一のオブジェクトにこのインターフェイスを実装する、 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)傍受した例外をサポートするインターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、`IDebugStackFrame2`をこのインターフェイスを取得するインターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 継承されたメソッドだけでなく[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)、`IDebugStackFrame3`次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|任意の通常の例外処理の前に、現在のスタック フレームの例外を処理します。|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|スタック アンワインドが発生した場合は、コードのコンテキストを返します。|  
  
## <a name="remarks"></a>Remarks  
 傍受した例外は、通常の例外処理ルーチンは、ランタイムによって呼び出される前に、デバッガーが例外を処理できることを意味します。 基本的に、例外をインターセプトは、例外ハンドラーがない場合にも存在が見かけ上の実行時のようになります。  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)すべて通常の例外コールバック イベント中に呼び出されます (唯一の例外は、デバッグするかどうか (マネージし、アンマネージ コード)、混在モードのコード中に例外をインターセプトできない場合、最終のコールバックの場合)。 デが実装していない場合`IDebugStackFrame3`、または、DE IDebugStackFrame3 からエラーが返されます::`InterceptCurrentException` (など`E_NOTIMPL`)、デバッガーが通常、例外を処理し、します。  
  
 例外をインターセプトすることで、デバッガーはデバッグ中のプログラムの状態に変更を加えるし、例外がスローされた時点での実行を再開するユーザーを許可できます。  
  
> [!NOTE]
>  インターセプトの例外は、共通言語ランタイム (CLR) 下で実行しているプログラムでは、マネージ コードでのみ許可されます。  
  
 デバッグ エンジンを示します"metricExceptions"を設定して例外をインターセプトをサポートしている値の 1 に実行時に使用して、`SetMetric`関数。 詳細については、次を参照してください。[デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)