---
title: "IDebugMessageEvent2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e61b6bae37b9e37dc9e448122f4595f3cba20f7f
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
このインターフェイスは、ユーザーからの応答を必要とする Visual Studio にメッセージを送信するデバッグ エンジン (DE) によって使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デでは、ユーザーからの応答を必要とする Visual Studio にメッセージを送信するには、このインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトのインターフェイスを実装する必要があります。 SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイスです。  
  
 このインターフェイスの実装での Visual Studio の呼び出しを通信する必要があります[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)デにします。 たとえば、DE のメッセージのスレッドの処理に投稿されたメッセージでこれ行うやこのインターフェイスを実装するオブジェクトでした、DE への参照を保持にコールバックする、DE に渡される応答に`IDebugMessageEvent2::SetResponse`です。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デを作成し、応答を要求するユーザーにメッセージを表示するには、このイベント オブジェクトを送信します。 使用して、イベントが送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)は、デバッグ中のプログラムに関連付けられている場合、SDM によって指定されたコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugMessageEvent2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|表示されるメッセージを取得します。|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|メッセージ ボックスから存在する場合、応答を設定します。|  
  
## <a name="remarks"></a>コメント  
 特定のメッセージのユーザーから特定の応答が必要な場合、デはこのインターフェイスを使用します。 など、DE では、リモートでプログラムにアタッチしようとすると、後、「アクセス拒否」メッセージを取得、デ メッセージを送信この特定の Visual Studio に、`IDebugMessageEvent2`イベント、メッセージ ボックス スタイル`MB_RETRYCANCEL`です。 これにより、ユーザーが再試行するか、アタッチ操作をキャンセルできます。  
  
 デでは、このメッセージの Win32 関数の規則に従うによって処理される方法を指定します`MessageBox`(を参照してください[AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)詳細)。  
  
 使用して、 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)インターフェイス ユーザーからの応答を必要としない Visual Studio にメッセージを送信します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)