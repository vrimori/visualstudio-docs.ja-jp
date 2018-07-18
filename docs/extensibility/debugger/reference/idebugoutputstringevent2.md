---
title: IDebugOutputStringEvent2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ac8a2072d801936d8035d5479c7d234082639818
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117122"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
このインターフェイスは、文字列を出力する、デバッグ エンジン (DE) によって、セッションのデバッグ マネージャー (SDM) に送信されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 文字列を送信するには、このインターフェイスを実装する、DE、**出力**IDE のウィンドウ。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトのインターフェイスを実装する必要があります。 SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デを作成し、このイベント オブジェクトに文字列を送信する送信、**出力**ウィンドウです。 使用して、イベントが送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)は、デバッグ中のプログラムに関連付けられている場合、SDM によって指定されたコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugOutputStringEvent2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|表示可能なメッセージを取得します。|  
  
## <a name="remarks"></a>コメント  
 たとえば、アンマネージ コードで出力する文字列開始できるはデバッグ中のプログラムは、Win32 に文字列を送信すると`OutputDebugString`関数。 この文字列は、DE によってインターセプトありとして SDM に送られる、`IDebugOutputStringEvent2`イベント。  
  
 使用して[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)ユーザーからの応答を必要とするメッセージを送信します。  
  
 使用して[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)応答が不要なエラー メッセージを送信します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)