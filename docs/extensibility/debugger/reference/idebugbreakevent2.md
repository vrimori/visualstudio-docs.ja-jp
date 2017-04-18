---
title: "IDebugBreakEvent2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 3eb66792461f9b31b1af5415a212130a07bb7b2c
ms.lasthandoff: 04/05/2017

---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
このインターフェイスは、非同期の中断が正常に完了したことをセッション デバッグ マネージャー (SDM) に指示します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デでは、プログラムでは改ページのユーザーをサポートするためにこのインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトのインターフェイスを実装する必要があります (、SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイス)。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 SDM 呼び出し[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)ユーザーが一時停止をデバッグするプログラムを要求したときにします。 プログラムが正常に一時停止されている、DE 送信、`IDebugBreakEvent2`イベント。 このイベントは、使用して送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムに添付するときに、SDM によって提供されるコールバック関数。  
  
## <a name="remarks"></a>コメント  
 たとえば、ユーザーが選択できる、**すべて中断**コマンドを**デバッグ**無限ループを実行しているプログラムのメニュー。 呼び出すことによって停止するプログラムに指示、SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)です。 DE 送信`IDebugBreakEvent2`プログラムが最後が停止します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
