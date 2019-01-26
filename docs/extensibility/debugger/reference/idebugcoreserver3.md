---
title: IDebugCoreServer3 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 388c884e77f4367eae1ac90e0390163efa7a7e37
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933066"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
このインターフェイスで、プロセスが実行されているサーバーに関する情報にアクセスできます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio では、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 使用[QueryInterface](/cpp/atl/queryinterface)からこのインターフェイスを取得する、 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)インターフェイス。 呼び出し[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)このインターフェイスを返すこともできます。 このインターフェイスは、(ローカルまたはリモート) のサーバー上のプログラムを起動するでカスタム ポートのサプライヤーによって最もよく使用されます。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 メソッドだけでなく、 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)インターフェイスでは、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|サーバーの名前を取得します。|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|サーバー名のフレンドリ バージョンを取得します。|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|これらのプロセスの開始時に自動的に、プロセスにアタッチする特定のデバッグ エンジンに指示します。|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|自動アタッチが失敗した場合は、特定のエラー コードを取得します。|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|サーバー上のデバッグ エンジンのインスタンスを作成します。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|サーバーが、呼び出し元と同じコンピューター上かどうかを示すフラグを取得します。|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|サーバーとの通信に使用されるプロトコルを示す値を取得します。|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|すべて無効には、このサーバーが認識するすべてのデバッグ エンジンの設定を自動-アタッチします。|  
  
## <a name="remarks"></a>Remarks  
 カスタム ポート供給業者が受信、 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)インターフェイスへの呼び出しで[イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)します。 `IDebugCoreServer3`インターフェイスは、そのインターフェイスから取得できます。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)