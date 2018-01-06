---
title: "IDebugThread2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2
helpviewer_keywords: IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dca773ca63e2ab6bbc852648d2dea92b0b9813d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
 このインターフェイスはブレークポイント要求を作成するのには使用も (を参照してください[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md))。  
  
 このインターフェイスは、ブレークポイントがバインドまたはエラーを解決するときにも返されます (を参照してください[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)と[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md))。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugThread2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|このスレッドのスタック フレームの一覧を取得します。|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|スレッドの名前を取得します。|  
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|スレッドの名前を設定します。|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|スレッドが実行されているプログラムを取得します。|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|特定のスタック フレームとコードのコンテキストに、次のステートメントを設定できるかどうかを決定します。|  
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|次のステートメントを特定のスタック フレームとコードのコンテキストに設定します。|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|システムのスレッド識別子を取得します。|  
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|スレッドを中断します。|  
|[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)|スレッドを再開します。|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|スレッドを記述するプロパティを取得します。|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|この物理スレッドに関連付けられている論理スレッドを取得します。|  
  
## <a name="remarks"></a>コメント  
 1 つの物理スレッドが 1 つ以上に、複数のプログラムで実行できるため、`IDebugThread2`複数のプログラムからは、同じ物理スレッドを表すことができます。  
  
 呼び出して、イベントが送信ブレークポイントまたは例外が発生したときに[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)です。 このメソッドの引数の 1 つは、`IDebugThread2`現在のスレッドを表すインターフェイス。 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)の取得に使用、 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)の現在のスタック フレームのインターフェイスです。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)