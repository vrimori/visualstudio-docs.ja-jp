---
title: IDebugProcessCreateEvent2 |Microsoft Docs
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
- IDebugProcessCreateEvent2
helpviewer_keywords:
- IDebugProcessCreateEvent2
ms.assetid: c660439d-8b23-4dbb-923e-ebb5e1d7edf5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9359590ab2987a917963cf6bc4862da09202433d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723811"
---
# <a name="idebugprocesscreateevent2"></a>IDebugProcessCreateEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、プロセスを起動するときに送信されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProcessCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) やカスタム ポート サプライヤーは、プロセスが作成されたことを報告するには、このインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトでインターフェイスを実装する必要があります。 SDM を使用して[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)にアクセスする、`IDebugEvent2`インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 DE、またはカスタムのポート サプライヤーは、作成し、プロセスの作成を報告するには、このイベント オブジェクトを送信します。 デを使用してこのイベントを送信する、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムにアタッチされているときに、SDM によって指定されたコールバック関数。 このイベントを使用してカスタム ポート サプライヤーに送信、 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)インターフェイス。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)

