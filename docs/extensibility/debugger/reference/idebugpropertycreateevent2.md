---
title: IDebugPropertyCreateEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b86ac1ba81a7d203177afdde302e8f32599ea698
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854972"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
このインターフェイスは、特定のドキュメントに関連付けられているプロパティを作成するときにデバッグ エンジン (DE) によって、セッション デバッグ マネージャー (SDM) に送信されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デは、プロパティが作成されたことを報告するには、このインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトでインターフェイスを実装する必要があります。 SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイス。 デがロードまたは作成されたスクリプトに関連付けられたプロパティを作成し、そのスクリプトは、IDE に表示する必要がある場合、このインターフェイスが実装されます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デは作成し、プロパティが作成されたレポートにこのイベント オブジェクトを送信します。 使用して、イベントが送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムにアタッチされているときに、SDM によって指定されたコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugPropertyCreateEvent2`インターフェイス。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|新しいプロパティを取得します。|  
  
## <a name="remarks"></a>Remarks  
 デが、更新するにはこのイベントを SDM に送信できますプロパティに特定のドキュメントまたは関連付けられているスクリプトがある場合、**スクリプト ドキュメント**ウィンドウ、ドキュメントの名前に置き換えます。 SDM を呼び出します[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)引数で`guidDocument`を取得する、`VARIANT`を含む、 [IUnknown](/cpp/atl/iunknown)ポインター。 SDM を呼び出します[QueryInterface](/cpp/atl/queryinterface)を取得するには、このポインターを[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)を更新するために使用するインターフェイス、**スクリプト ドキュメント**ウィンドウ。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)