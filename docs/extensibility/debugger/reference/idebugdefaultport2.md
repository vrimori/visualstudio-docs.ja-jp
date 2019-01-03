---
title: IDebugDefaultPort2 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 3f371eb040ae2c160582093f07eacb2108bcb7b7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930584"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
このインターフェイスは、ポートのサーバーおよび通知の機能にアクセスするためのいくつかのメソッドを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio では、プログラムにアクセスするためのデバッグ ポートを表すためには、このインターフェイスを実装します。 カスタム ポート サプライヤーは、リモート デバッグを処理する場合、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 メソッドの引数、 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)インターフェイスは、このインターフェイスを提供します。 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)インターフェイスは、このインターフェイスを取得できます。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
 定義されている方法だけでなく[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|このポートからポート通知インターフェイスを取得します。|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|このポートをホストするサーバーに、インターフェイスを取得します。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|このポートが、ローカル コンピューターで実行されているかどうかを判断します。|  
  
## <a name="remarks"></a>Remarks  
 名前"`IDebugDefaultPort2`"不適切な名称、少しは既定のポートはありません。 "IDebugPort3"が呼び出される可能性があります。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)