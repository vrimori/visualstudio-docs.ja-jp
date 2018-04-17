---
title: IDebugProcessQueryProperties |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ac071afd9f9ce7d45a05408aeec32117776832f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
このインターフェイスはによって実装される拡張機能インターフェイス[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)実装します。 これにより、デバッグ プロセス環境に関する情報を取得する実行者できます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ プロセスの実行環境に関する情報を取得するには、このインターフェイスを実装します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProcessQueryProperties`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|プロパティの値を照会します。|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|プロパティの値を照会します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは実装はほとんどありません。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)