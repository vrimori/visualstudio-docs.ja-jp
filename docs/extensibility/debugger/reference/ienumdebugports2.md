---
title: "IEnumDebugPorts2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 277189c9b5510df1da4802e42225ffafa4b6995c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
このインターフェイスは、コンピューターまたはポートの仕入先のポートを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 カスタム ポート仕入先では、供給業者によって作成されたポートの一覧を表すためには、このインターフェイスを実装します。 Visual Studio では、独自のポートのサプライヤーをサポートするためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)ポート業者によって作成されたポートのリストを表す、このインターフェイスを取得します。 呼び出す[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)保存されたポートの一覧を表す、このインターフェイスを取得するディスクにします。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumDebugPorts2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|列挙のシーケンス内のポートの指定した数を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|指定した列挙のシーケンス内のポート数をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|列挙のシーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|現在の列挙子と同じ列挙の状態を含む列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|列挙子では、ポートの数を取得します。|  
  
## <a name="remarks"></a>コメント  
 Visual Studio では、このインターフェイスを使用して、プロセスにアタッチするために使用されるポートの一覧を設定します。  
  
 通常、デバッグ エンジンにはこのインターフェイスは使いません。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)