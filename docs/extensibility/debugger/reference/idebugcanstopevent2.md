---
title: IDebugCanStopEvent2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 48f049648fcbd93d7ad7411a4dfeba8bbdb4431d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105607"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
このインターフェイスを使用すると、セッション デバッグ マネージャー (SDM) を現在のコードの場所で停止するかどうか確認します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) では、ソース コードをステップ実行をサポートするためにこのインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトのインターフェイスを実装する必要があります (、SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイス)。  
  
 このインターフェイスの実装の SDM の呼び出しを通信する必要があります[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)デバッグ エンジンにします。 デバッグ エンジンのメッセージのスレッドの処理に投稿されたメッセージでこれ行うなど、このインターフェイスを実装するオブジェクトがデバッグ エンジンに参照を保持しに渡されたフラグを使って、デバッグ エンジンにコールバック`IDebugCanStopEvent2::CanStop`です。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このメソッド、DE が実行して、DE を継続する要求するたびに、コードのステップ実行、DE を送信できます。 このイベントは、使用して送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムに添付するときに、SDM によって提供されるコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugCanStopEvent2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|このイベントの理由を取得します。|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|デバッグ中のプログラムがこのイベント (と停止の理由を説明するイベントの送信) の場所で停止するかのみの実行を続行するかどうかを指定します。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|このイベントの場所を記述したドキュメントのコンテキストを取得します。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|このイベントの場所を記述したコードのコンテキストを取得します。|  
  
## <a name="remarks"></a>コメント  
 デは、関数と、DE にユーザーの手順がデバッグ情報が検出されないやデバッグ情報が存在しても、DE がソース コードがその場所に対して表示されるかどうかを把握していない場合、このインターフェイスを送信します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)