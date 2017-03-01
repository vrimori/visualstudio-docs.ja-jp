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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 0f033c5793dc3b89a1f2bd74a2bc4857730fb746
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
このインターフェイスは、ユーザーからの応答を必要とする Visual Studio にメッセージを送信するデバッグ エンジン (DE) によって使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デでは、ユーザーからの応答を必要とする Visual Studio にメッセージを送信するには、このインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)インターフェイスは、このインターフェイスと同じオブジェクトに実装する必要があります。 SDM を使用して[QueryInterface](/visual-cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイスです。  
  
 このインターフェイスの実装での Visual Studio の呼び出しを伝える必要があります[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)デにします。 たとえば、DE のメッセージの処理、スレッドに投稿されたメッセージとそのためもこのインターフェイスを実装するオブジェクトでした、DE への参照を保持に渡された応答を使用して、DE にコールバック`IDebugMessageEvent2::SetResponse`します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デを作成し、応答を要求するユーザーにメッセージを表示するには、このイベント オブジェクトを送信します。 使用して、イベントが送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムに関連付けられている場合に、SDM によって提供されるコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、のメソッドを示しています。`IDebugMessageEvent2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|表示されるメッセージを取得します。|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|メッセージ ボックス、発生した場合、応答を設定します。|  
  
## <a name="remarks"></a>コメント  
 特定のメッセージのユーザーから特定の応答が必要な場合、デはこのインターフェイスを使用します。 など、DE では、リモートでプログラムにアタッチしようした後、「アクセス拒否」メッセージを取得、DE、この特定はメッセージを送信 Visual Studio で、`IDebugMessageEvent2`イベント メッセージ ボックスのスタイルと`MB_RETRYCANCEL`です。 これにより、ユーザーが再試行するか、またはアタッチ操作をキャンセルできます。  
  
 デでは、このメッセージの Win32 関数の規則に従って処理する方法を指定`MessageBox`(を参照してください[AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8)詳細)。  
  
 使用して、 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)をユーザーからの応答を必要としない Visual Studio にメッセージを送信するインターフェイスです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
