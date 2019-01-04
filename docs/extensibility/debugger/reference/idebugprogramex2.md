---
title: IDebugProgramEx2 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 3131dae9d9bf715d3927f9654224cab3d6a36d53
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907885"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
このインターフェイスにより、セッション デバッグ マネージャー (SDM) プログラムにアタッチし、プログラムに関連付けられたプログラムのノードを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 カスタム ポート サプライヤーと同じオブジェクトでこのインターフェイスを実装する、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス SDM を同時にすべてのセッションを追跡するためにポート サプライヤーの許可にアタッチされている間に、プログラムにアタッチできるようにするには、プログラム。 カスタム ポート サプライヤーは、選択した場合、このインターフェイスを実装できます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 SDM コール[QueryInterface](/cpp/atl/queryinterface)上、`IDebugProgram2`インターフェイス プログラムがアタッチされているセッションを追跡するには、このインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProgramEx2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[添付](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|プログラムをセッションにアタッチします。|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|プログラムに関連付けられているプログラムのノードを取得します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスは、SDM とプログラムの間にプライベートです。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Portpriv.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)