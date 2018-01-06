---
title: "IDebugDefaultPort2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDefaultPort2
helpviewer_keywords: IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e2a388d25ec828eeedb5c86860ad697848a5cb77
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)