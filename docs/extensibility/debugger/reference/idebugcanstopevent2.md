---
title: IDebugCanStopEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2609ca6cdf06117da56572c3574426a6d68c9178
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987948"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
このインターフェイスは、現在のコードの場所で停止するかどうか、セッション デバッグ マネージャー (SDM) を確認に使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、ソース コードをステップ実行をサポートするためにこのインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトでインターフェイスを実装する必要があります (、SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイス)。  
  
 このインターフェイスの実装の SDM の呼び出しを通信する必要があります[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)デバッグ エンジンにします。 たとえば、デバッグ エンジンのメッセージの処理スレッドに投稿されたメッセージを表示できますまたはこのインターフェイスを実装するオブジェクトがデバッグ エンジンに参照を保持しに渡されたフラグを使用して、デバッグ エンジンにコールバック`IDebugCanStopEvent2::CanStop`します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このメソッドを実行し、DE、DE が寄せられるたびにはコードをステップ実行、DE を送信できます。 このイベントを使用して、送信、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムに添付するときに、SDM によって提供されるコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugCanStopEvent2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|このイベントの理由を取得します。|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|デバッグ中のプログラムがこのイベント (と停止の理由を説明するイベントの送信) の場所で停止する必要があるかどうか、または実行を続けるかどうかを指定します。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|このイベントの場所を説明するドキュメント コンテキストを取得します。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|このイベントの場所を記述したコードのコンテキストを取得します。|  
  
## <a name="remarks"></a>Remarks  
 デは、関数と、DE にユーザーの手順がデバッグ情報が検出されないまたはデバッグ情報が存在するが、DE はその場所へのソース コードを表示できるかどうかを認識していない場合、このインターフェイスを送信します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)