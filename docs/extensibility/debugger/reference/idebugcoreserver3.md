---
title: IDebugCoreServer3 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5066521dbed42790d508becc1a3591dff3ae559d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108532"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
このインターフェイスは、プロセスを実行するサーバーに関する情報へのアクセスを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio では、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 使用して[QueryInterface](/cpp/atl/queryinterface)からこのインターフェイスを取得、 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)インターフェイスです。 呼び出し[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)このインターフェイスを返すこともできます。 (ローカルまたはリモート)、サーバー上のプログラムを起動する、カスタム ポート業者によって、最も多くの場合、このインターフェイスが使用されます。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 メソッドだけでなく、 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)インターフェイス、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|サーバーの名前を取得します。|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|サーバー名の親しみやすいバージョンを取得します|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|これらのプロセスの開始時に自動的にプロセスにアタッチする特定のデバッグ エンジンに指示します。|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|自動アタッチが失敗した場合は、特定のエラー コードを取得します。|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|サーバー上のデバッグ エンジンのインスタンスを作成します。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|サーバーが、呼び出し元と同じコンピューター上かどうかを示すフラグを取得します。|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|サーバーとの通信に使用されているプロトコルを示す値を取得します。|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|無効にすべてのオート アタッチに関するこのサーバーを知っているすべてのデバッグ エンジンの設定。|  
  
## <a name="remarks"></a>コメント  
 カスタム ポート供給業者が受信、 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)インターフェイスへの呼び出しで[イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)です。 `IDebugCoreServer3`インターフェイスは、そのインターフェイスから取得できます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)