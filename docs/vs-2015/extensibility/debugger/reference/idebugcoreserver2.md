---
title: IDebugCoreServer2 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 98d25bb44c678d7c81ab421d3ef5fd2b4aa2e246
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276459"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスを表し、ネットワーク上のコンピューター上のサーバーからの情報の取得に使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio では、サーバーを表すためには、このインターフェイスを実装します。 Visual Studio の各インスタンスは、このインターフェイスのインスタンスを作成します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 カスタム ポート サプライヤーへの呼び出しでこのインターフェイスの受信[イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)します。  
  
 デバッグ エンジンとして使用できるは、このインターフェイスへの呼び出しを通じて間接的に[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (返された[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)、インターフェイスから派生した`IDebugCoreServer2`)。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugCoreServer2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|マシンの属性と名前を取得します。|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|コンピューターの名前を取得します。|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|コンピューター上に存在するポートのサプライヤーを取得します。|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|コンピューターに既に存在するポートを取得します。|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|コンピューター上のすべてのポートの列挙子を作成します。|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|コンピューター上のすべてのポート サプライヤーの列挙子を作成します。|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|マシンのマシン ユーティリティを取得します。|  
  
## <a name="remarks"></a>Remarks  
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

