---
title: "IDebugThread2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
caps.latest.revision: 12
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 363f2aa684d45a07978c70b222af7f35ea2b05d3
ms.lasthandoff: 02/22/2017

---
# <a name="idebugthread2"></a>IDebugThread2
このインターフェイスは、プログラムで実行中のスレッドを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugThread2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) では、1 つのプログラムの実行のスレッドを表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)現在アクティブなスレッドを表す、このインターフェイスを取得します。  
  
 このインターフェイスはブレークポイント リクエストの作成にも使用 (を参照してください[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md))。  
  
 このインターフェイスは、バインド、またはエラーのブレークポイントを解決するときにも返されます (を参照してください[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)と[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md))。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、のメソッドを示しています。`IDebugThread2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|このスレッドのスタック フレームの一覧を取得します。|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|スレッドの名前を取得します。|  
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|スレッドの名前を設定します。|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|スレッドが実行されているプログラムを取得します。|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|特定のスタック フレームとコードのコンテキストに、次のステートメントを設定できるかどうかを決定します。|  
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|次のステートメントを特定のスタック フレームおよびコードのコンテキストに設定します。|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|システムのスレッド識別子を取得します。|  
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|スレッドを中断します。|  
|[再開](../../../extensibility/debugger/reference/idebugthread2-resume.md)|スレッドを再開します。|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|スレッドを記述するプロパティを取得します。|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|この物理スレッドに関連付けられている論理スレッドを取得します。|  
  
## <a name="remarks"></a>コメント  
 1 つの物理スレッドが&1; つ以上複数のプログラムで実行できるため`IDebugThread2`複数のプログラムからは同じ物理スレッドを表すことができます。  
  
 ブレークポイントまたは例外が発生すると、呼び出すことによってイベントが送信[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)です。 このメソッドの引数の&1; つは、`IDebugThread2`現在のスレッドを表すインターフェイスです。 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)取得に使用される、 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)現在のスタック フレームのインターフェイスです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
