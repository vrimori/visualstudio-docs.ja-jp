---
title: IDebugPortEvents2 |Microsoft Docs
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
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3eb6208d815e4951bd916d014cddfdda34a8e589
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539065"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugPortEvents2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportevents2)します。  
  
このインターフェイスは、プロセスとプログラムの作成と破棄を特定のポートでのリスナー (通常、セッション デバッグ マネージャー [SDM] またはデバッグ エンジン) を通知します。 この情報は、ポートで実行されるプログラム、プロセスのリアルタイム ビューに表示できます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio は、通常、プログラムの作成と破棄に関する通知を受信するには、このインターフェイスを実装します。 デバッグ エンジンは、このようなポート イベントをリッスンするには、このインターフェイスを実装もできます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 すべて[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)のインターフェイスを照会できます、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>インターフェイス。 次に、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A>メソッドの`IDebugPortEvents2`で呼び出される、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>インターフェイスを取得する、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>インターフェイス。 最後に、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>メソッドで、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>インターフェイスが呼び出され、イベントを送信して、[イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)メソッド。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugPortEvents2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|作成とプロセスと、ポート上のプログラムの破棄を記述するイベントを送信します。|  
  
## <a name="remarks"></a>Remarks  
 `IDebugPortEvents2` 既にデバッグ中のプロセスで実行されるプログラムをデバッグする、SDM によってもに使用します。  
  
 ポート イベントは、このインターフェイスによって、SDM に渡されます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

