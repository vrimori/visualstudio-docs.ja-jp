---
title: IDebugProgramCreateEvent2 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cd69afea6723050478f1b91d9b298a893b6ceceb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302602"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、プログラムに関連付けられている場合にデバッグ エンジン (DE) によって、セッション デバッグ マネージャー (SDM) に送信されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デやカスタム ポート サプライヤーは、プログラムが作成されたこと、通常、プログラムにアタッチ時に報告するには、このインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトでインターフェイスを実装する必要があります。 SDM を使用して、`QueryInterface`メソッドにアクセスする、`IDebugEvent2`インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 DE、またはカスタムのポート サプライヤーは、作成し、プログラムの作成を報告するには、このイベント オブジェクトを送信します。 デを使用してこのイベントを送信する、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムに添付するときに、SDM によって指定されたコールバック関数。 このイベントを使用してカスタム ポート サプライヤーに送信、 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)インターフェイス。  
  
## <a name="remarks"></a>Remarks  
 DE またはカスタムのポート サプライヤーは、新しい発行[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)呼び出してインターフェイス[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

