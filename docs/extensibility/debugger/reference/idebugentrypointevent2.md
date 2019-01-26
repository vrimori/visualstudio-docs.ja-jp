---
title: IDebugEntryPointEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2205ef7d6fa8b270ce30224f867dd2c318272b37
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992283"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
デバッグ エンジン (DE) では、プログラムがユーザー コードの最初の命令を実行するときに、このインターフェイスがセッション デバッグ マネージャー (SDM) を送信します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デが通常の操作の一部としてこのインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトでインターフェイスを実装する必要があります。 SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デでは、作成し、デバッグ中のプログラムが読み込まれ、ユーザー コードの最初の命令を実行する準備ができて、このイベント オブジェクトを送信します。 使用して、イベントが送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムに添付するときに、SDM によって指定されたコールバック関数。  
  
## <a name="remarks"></a>Remarks  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)プログラムが最初の命令を実行するときに送信されます。 たとえば、`IDebugEntryPoint2`プログラムがユーザーを実行するときに送信`main`関数。  
  
 ドイツが送信すると`IDebugEntryPointEvent2`、コードの現在の位置がなどのユーザー コードの最初の命令にする必要があります`main`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)