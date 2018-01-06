---
title: "IDebugEngine3 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3
helpviewer_keywords: IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f601cd38b5546d79f97e1c15a7c33c5de7df5d03
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine3"></a>IDebugEngine3
1 つまたは複数のモジュールのデバッグを制御する 1 つのデバッグ エンジン (DE) を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは実装によってカスタム DE (シンボルがサポートしている) 場合 JustMyCode 状態を有効にします。 シンボルと JustMyCode をサポートしている場合、DE によってこのインターフェイスを実装する必要があります。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、セッションのデバッグ マネージャーのシンボルの読み込み元の場所のオプションをユーザーに渡すには、(SDM) によって呼び出されます。 インスタンス化されるときに、エンジンの GUID を設定するために呼び出されます (この GUID はエンジンの登録時の測度に基づく)。 SDM も JustMyCode 状態を設定して、指定された状態にデバッガーによって把握されているすべての例外を設定する、このインターフェイスを呼び出します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 継承されたメソッドだけでなく[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)、`IDebugEngine3`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|デがデバッグ シンボルの検索に使用するパスまたはパスを設定します。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|シンボルが読み込まれてしていないすべてのモジュールのシンボルを読み込みます。|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|JustMyCode 情報について、DE に指示します。|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|メトリックから DE GUID を設定します。|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|指定された状態に、現在未処理のすべての例外を設定します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)