---
title: IDebugDefaultPort2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6d131ab24cc57af1846f89b61afa2d89ae2cacb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106904"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
このインターフェイスは、ポートのサーバーおよび通知の機能にアクセスするためのいくつかのメソッドを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio では、プログラムにアクセスするためのデバッグ ポートを表すためには、このインターフェイスを実装します。 カスタム ポートのサプライヤーは、リモート デバッグを処理する場合、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 上のメソッドに渡す引数、 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)インターフェイスは、このインターフェイスを提供します。 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)インターフェイスは、このインターフェイスにも取得できます。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 定義されているメソッドだけでなく[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|このポートからポート通知インターフェイスを取得します。|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|このポートをホストしているサーバーへのインターフェイスを取得します。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|このポートが、ローカル コンピューターで実行されているかどうかを判断します。|  
  
## <a name="remarks"></a>コメント  
 名前"`IDebugDefaultPort2`"、名称のビットは、既定のポートは表しません。 "IDebugPort3"が呼び出される可能性があります。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)