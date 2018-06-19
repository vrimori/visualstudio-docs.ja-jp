---
title: IDebugProgramEx2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8e26a21e00ff9f0fff664130171a302667ee414
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120963"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
このインターフェイスにより、セッション デバッグ マネージャー (SDM) がプログラムにアタッチし、プログラムに関連付けられているプログラムのノードを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 カスタム ポート業者と同じオブジェクトでこのインターフェイスを実装する、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス SDM を同時に許可するすべてのセッションを追跡するためにポート サプライヤーにアタッチされている間に、プログラムにアタッチできるようにするために、プログラムです。 カスタム ポート サプライヤーは、選択した場合、このインターフェイスを実装できます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 SDM 呼び出し[QueryInterface](/cpp/atl/queryinterface)上、`IDebugProgram2`インターフェイスをプログラムに関連付けられているセッションを追跡するには、このインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProgramEx2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[添付](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|プログラムをセッションにアタッチします。|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|プログラムに関連付けられているプログラムのノードを取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、SDM とプログラムの間にプライベートです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)