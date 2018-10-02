---
title: IDebugCoreServer3 |Microsoft Docs
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
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1c039ccb08f7143112939f9d7880d508bd079a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47549167"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugCoreServer3](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcoreserver3)します。  
  
このインターフェイスで、プロセスが実行されているサーバーに関する情報にアクセスできます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio では、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 使用[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)からこのインターフェイスを取得する、 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)インターフェイス。 呼び出し[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)このインターフェイスを返すこともできます。 このインターフェイスは、(ローカルまたはリモート) のサーバー上のプログラムを起動するでカスタム ポートのサプライヤーによって最もよく使用されます。  
  
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
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)

