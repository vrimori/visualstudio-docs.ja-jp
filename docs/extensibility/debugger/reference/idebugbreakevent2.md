---
title: IDebugBreakEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d23a8c534ba3d829a02075d2d195689df6d08482
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857505"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
このインターフェイスは、非同期の中断が正常に完了したことをセッション デバッグ マネージャー (SDM) に指示します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デでは、プログラムでユーザーの中断をサポートするためにこのインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトでインターフェイスを実装する必要があります (、SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイス)。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 SDM コール[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)ユーザーが一時停止するデバッグ中のプログラムを要求された場合。 プログラムが正常に一時停止されて、DE 送信、`IDebugBreakEvent2`イベント。 このイベントを使用して、送信、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムに添付するときに、SDM によって提供されるコールバック関数。  
  
## <a name="remarks"></a>Remarks  
 たとえば、ユーザーが選択できる、**すべて中断**コマンドを**デバッグ**無限ループを実行しているプログラムから抜け出すメニュー。 プログラムに対して呼び出すことによって停止を指示、SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)します。 DE 送信`IDebugBreakEvent2`プログラムが最後に停止します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)