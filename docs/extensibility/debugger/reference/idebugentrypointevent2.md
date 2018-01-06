---
title: "IDebugEntryPointEvent2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEntryPointEvent2
helpviewer_keywords: IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ed45b6d0166a92e9547b7ad76e189108cd2b5e02
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
デバッグ エンジン (DE) は、プログラムがユーザー コードの最初の命令を実行しようとしていますが、セッションのデバッグ マネージャー (SDM) をこのインターフェイスを送信します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 DE、通常の運用の一環としてこのインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトのインターフェイスを実装する必要があります。 SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デは、作成し、デバッグ中のプログラムが読み込まれているし、ユーザー コードの最初の命令を実行する準備ができてときに、このイベント オブジェクトを送信します。 使用して、イベントが送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)は、デバッグ中のプログラムに添付するときに、SDM によって指定されたコールバック関数。  
  
## <a name="remarks"></a>コメント  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)を非常に最初の命令を実行するプログラムは、ときに送信されます。 たとえば、`IDebugEntryPoint2`プログラムをユーザーを実行する場合、送信`main`関数。  
  
 デが送信すると`IDebugEntryPointEvent2`、コードの現在の位置がなどのユーザー コードの最初の命令にする必要があります`main`です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)