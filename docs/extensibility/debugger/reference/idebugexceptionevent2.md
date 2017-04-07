---
title: "IDebugExceptionEvent2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: c9817ca386846833ab022c5dbca3d3807bd38ef6
ms.lasthandoff: 04/05/2017

---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
デバッグ エンジン (DE) は、現在実行されているプログラムでは、例外がスローされたときに、セッションのデバッグ マネージャー (SDM) をこのインターフェイスを送信します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デでは、デバッグ中のプログラムで例外が発生したことをレポートには、このインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトのインターフェイスを実装する必要があります。 SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デを作成し、例外を報告するには、このイベント オブジェクトを送信します。 使用して、イベントを送信、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)は、デバッグ中のプログラムに添付するときに、SDM によって指定されたコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugExceptionEvent2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|このイベントを発生させた例外に関する詳細情報を取得します。|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|このイベントを発生させたスローされる例外の人間が判読できる説明を取得します。|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|デバッグ エンジン (DE) が実行を再開したときにデバッグするプログラムにこの例外を渡すことのオプションをサポートしているかどうかを判断します。|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|例外を破棄する必要がある場合または実行が再開したときにデバッグするプログラムを例外を渡す必要があるかどうかを指定します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>コメント  
 イベントを送信する前に、DE が確認するまでかどうかはこの例外イベントで指定された初回またはセカンド チャンス例外を前回呼び出した[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)です。 最初の例外に指定されている場合、`IDebugExceptionEvent2`イベントは、SDM に送信します。 それ以外の場合は、DE にアプリケーション例外を処理する機会が得られます。 例外ハンドラーが指定されていない場合、例外は次の例外として指定されている場合、`IDebugExceptionEvent2`イベントは、SDM に送信します。 それ以外の場合、DE、プログラムの実行を再開して、オペレーティング システムまたはランタイムが例外を処理します。  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
