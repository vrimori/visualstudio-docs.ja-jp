---
title: IDebugThread2 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e1166264e83ffe07bbdb7e55b8cff3b296f67a56
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755600"
---
# <a name="idebugthread2"></a>IDebugThread2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、プログラムで実行されているスレッドを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugThread2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、1 つのプログラム実行のスレッドを表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)現在アクティブなスレッドを表す、このインターフェイスを取得します。  
  
 このインターフェイスはブレークポイント要求の作成にも使用されます (を参照してください[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md))。  
  
 このインターフェイスは、ブレークポイントがバインドまたはエラーを解決するときにも返されます (を参照してください[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)と[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md))。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugThread2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|このスレッドのスタック フレームの一覧を取得します。|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|スレッドの名前を取得します。|  
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|スレッドの名前を設定します。|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|スレッドが実行されているプログラムを取得します。|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|次のステートメントを特定のスタック フレームとコードのコンテキストに設定できるかどうかを判断します。|  
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|特定のスタック フレームとコードのコンテキストには、次のステートメントを設定します。|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|システムのスレッド識別子を取得します。|  
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|スレッドを中断します。|  
|[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)|スレッドを再開します。|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|スレッドを記述するプロパティを取得します。|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|この物理スレッドに関連付けられている論理スレッドを取得します。|  
  
## <a name="remarks"></a>Remarks  
 1 つの物理スレッドが 1 つ以上複数のプログラムで実行できるため、 `IDebugThread2` 1 つ以上のプログラムからは、同じ物理スレッドを表すことができます。  
  
 呼び出すことによって、イベントが送信ブレークポイントまたは例外が発生したときに[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)します。 このメソッドの引数の 1 つは、`IDebugThread2`現在のスレッドを表すインターフェイス。 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)を取得するために使用、 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)現在のスタック フレームのインターフェイス。  
  
## <a name="requirements"></a>必要条件  
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

