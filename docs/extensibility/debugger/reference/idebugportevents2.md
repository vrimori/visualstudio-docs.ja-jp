---
title: IDebugPortEvents2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af2652bd18ff5d371389e8d3a7d3ab4c477eaa34
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120037"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
このインターフェイスは、プロセスとプログラムの作成と破棄、特定のポートでのリスナー (通常、セッション デバッグ マネージャー [SDM] またはデバッグ エンジン) を通知します。 この情報は、プロセスとポートで実行されているプログラムのリアルタイム ビューを表示する使用できます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio は、通常、プログラムの作成と破棄に関する通知を受信するには、このインターフェイスを実装します。 デバッグ エンジンは、このようなポート イベントをリッスンするには、このインターフェイスを実装もできます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 すべて[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)のインターフェイスを照会できる、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>インターフェイスです。 続いて、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A>メソッドを`IDebugPortEvents2`で呼び出される、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>取得するインターフェイス、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>インターフェイスです。 最後に、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>メソッドで、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>インターフェイスがを介してイベントを送信するために呼び出される、[イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)メソッドです。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugPortEvents2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|作成とプロセスと、ポート上のプログラムの破棄を説明するイベントを送信します。|  
  
## <a name="remarks"></a>コメント  
 `IDebugPortEvents2` 使用されますが、SDM は既にデバッグ中のプロセスで実行されるプログラムをデバッグします。  
  
 ポート イベントは、このインターフェイスで、SDM に渡されます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)