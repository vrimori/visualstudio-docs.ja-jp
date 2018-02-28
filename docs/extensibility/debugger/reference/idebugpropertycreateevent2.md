---
title: "IDebugPropertyCreateEvent2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0557fd39d21415dfddb1a571c4f9e6ee69badf10
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
このインターフェイスは、特定のドキュメントに関連付けられているプロパティの作成時に、セッションのデバッグ マネージャー (SDM) にデバッグ エンジン (DE) によって送信されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デでは、プロパティが作成されたことを報告するには、このインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトのインターフェイスを実装する必要があります。 SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイスです。 デが読み込まれたまたは作成されたスクリプトに関連付けられたプロパティを作成し、そのスクリプトは、IDE に表示される必要がある場合、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デは、作成し、このイベント オブジェクトのプロパティが作成されたレポートに送信します。 使用して、イベントが送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)は、デバッグ中のプログラムに関連付けられている場合、SDM によって指定されたコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugPropertyCreateEvent2`インターフェイスです。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|新しいプロパティを取得します。|  
  
## <a name="remarks"></a>コメント  
 プロパティに特定のドキュメントまたはそれに関連付けられているスクリプトがある場合、DE できますこのにイベントを送信、SDM を更新するために、**スクリプト ドキュメント**ドキュメントの名前を持つウィンドウです。 SDM が呼び出す[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)引数と共に`guidDocument`を取得する、`VARIANT`を含む、 [IUnknown](/cpp/atl/iunknown)ポインター。 SDM が呼び出す[QueryInterface](/cpp/atl/queryinterface)を取得するには、このポインター上、 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)の更新に使用するインターフェイス、**スクリプト ドキュメント**ウィンドウです。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)