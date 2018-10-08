---
title: IDebugMessageEvent2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: adb1b46cceeabb7d1d370dc18117f1995d52aee7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536969"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugMessageEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmessageevent2)します。  
  
このインターフェイスは、ユーザーからの応答を必要とする Visual Studio にメッセージを送信するデバッグ エンジン (DE) によって使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デでは、ユーザーの応答を必要とする Visual Studio にメッセージを送信するには、このインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトでインターフェイスを実装する必要があります。 SDM を使用して[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)にアクセスする、`IDebugEvent2`インターフェイス。  
  
 このインターフェイスの実装での Visual Studio の呼び出しを通信する必要があります[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) DE にします。 DE のメッセージの処理スレッドに投稿されたメッセージを表示できますなど、このインターフェイスを実装するオブジェクトはでした、DE への参照を保持しに渡される応答と共に、DE にコールバック`IDebugMessageEvent2::SetResponse`します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デは作成し、応答を要求するユーザーにメッセージを表示するには、このイベント オブジェクトを送信します。 使用して、イベントが送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムにアタッチされているときに、SDM によって指定されたコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugMessageEvent2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|表示するメッセージを取得します。|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|メッセージ ボックスから存在する場合、応答を設定します。|  
  
## <a name="remarks"></a>Remarks  
 デは、特定のメッセージのユーザーから特定の応答が必要な場合に、このインターフェイスを使用します。 たとえば、プログラムをリモートで接続を試行した後、「アクセス拒否」メッセージを取得する、DE 場合、DE この特定のメッセージに送信で Visual Studio、`IDebugMessageEvent2`イベント、メッセージ ボックスのスタイルを`MB_RETRYCANCEL`します。 これにより、再試行またはアタッチ操作をキャンセルするユーザー。  
  
 デでは、このメッセージの Win32 関数の規則に従うによって処理される方法を指定します`MessageBox`(を参照してください[AfxMessageBox](http://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8)詳細については)。  
  
 使用して、 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)インターフェイス ユーザーからの応答を必要としない Visual Studio にメッセージを送信します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)

