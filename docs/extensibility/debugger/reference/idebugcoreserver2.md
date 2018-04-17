---
title: IDebugCoreServer2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce3e4c0c933527a5db754dcd96de97283e6e8260
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
このインターフェイスを表し、ネットワーク上のコンピューター上のサーバーから情報を取得に使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio では、サーバーを表すためには、このインターフェイスを実装します。 Visual Studio の各インスタンスでは、このインターフェイスのインスタンスを作成します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 カスタム ポート業者への呼び出しでこのインターフェイスを受信する[イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)です。  
  
 デバッグ エンジンとして使用できるは、このインターフェイスへの呼び出しを通じて間接的に[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (返された[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)から派生したインターフェイス`IDebugCoreServer2`)。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugCoreServer2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|コンピューターの属性と名前を取得します。|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|コンピューターの名前を取得します。|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|コンピューター上に存在するポートのサプライヤーを取得します。|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|コンピューターに既に存在するポートを取得します。|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|コンピューター上のすべてのポートの列挙子を作成します。|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|マシン上のすべてのポート仕入先の列挙子を作成します。|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|コンピューターのマシン ユーティリティを取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、ネットワーク上のマシンで実行されているプロセスを参照する Visual Studio によっても使用されます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)