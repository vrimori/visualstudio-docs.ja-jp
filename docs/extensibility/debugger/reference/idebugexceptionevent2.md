---
title: IDebugExceptionEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1348e83a3b07240fcb1c5e6ae4819ea85e4c054
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53929879"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
デバッグ エンジン (DE) では、現在実行中のプログラムで例外がスローされたときに、このインターフェイスをセッション デバッグ マネージャー (SDM) に送信します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デでは、デバッグ中のプログラムで例外が発生したことをレポートには、このインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトでインターフェイスを実装する必要があります。 SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デは作成し、例外を報告するには、このイベント オブジェクトを送信します。 使用して、イベントを送信、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムに添付するときに、SDM によって指定されたコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugExceptionEvent2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|このイベントを発生させた例外に関する詳細な情報を取得します。|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|このイベントを発生させたスローされる例外の人間が判読できる説明を取得します。|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|デバッグ エンジン (DE) に実行が再開されるときにデバッグするプログラムにこの例外を渡すことがサポートしているかどうかを判断します。|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|例外を破棄する場合または実行の再開時にデバッグ中のプログラムを例外を渡す必要があるかどうかを指定します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Remarks  
 イベントを送信する前に、DE はかどうかはこの例外イベントで指定された初回またはセカンド チャンス例外を以前の呼び出しを確認します。 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)します。 ファースト チャンス例外として指定されている場合、`IDebugExceptionEvent2`イベントは、SDM に送信します。 それ以外の場合は、DE は、アプリケーション例外を処理する機会を与えます。 例外ハンドラーが指定されていない場合、次の例外として、例外が指定されている場合、`IDebugExceptionEvent2`イベントは、SDM に送信します。 それ以外の場合、DE、プログラムの実行を再開して、オペレーティング システムやランタイムの例外を処理します。  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)