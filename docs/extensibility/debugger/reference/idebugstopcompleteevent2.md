---
title: "IDebugStopCompleteEvent2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 6
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 55061440f4690c9b9f9b7a90dc5474391f908046
ms.lasthandoff: 02/22/2017

---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
デバッグ エンジン (DE) は、プログラムが停止した場合は、このオプションのイベントをセッション デバッグ マネージャー (SDM) に送信できます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 これは、新しいインターフェイスの[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]です。 以前のリリースでは、非同期の停止はサポートしませんでした。  
  
 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)マルチ プロセスや複数のプログラムのシナリオで SDM によって呼び出されます。 1 つのプログラムは、停止イベントを SDM に送信するときに、SDM を停止するには、他のプログラムを要求します。  
  
 プログラムが停止したという SDM を非同期的に通知に使用されます。 場所もコードが実行されていないデバッグ対象のプログラム内、これはインタープリター デバッグ エンジンでは、便利なので[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)同期的に完了できません。 返す必要があるデバッグ エンジンがこの非同期通知を使用するか、`S_ASYNC_STOP`から[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll
