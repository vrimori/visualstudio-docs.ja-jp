---
title: "IDebugModule3 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1db551b9f62fbf85cd996e5f14bdb95c5aaca1f2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule3"></a>IDebugModule3
このインターフェイスは、シンボルと JustMyCode 状態の別の場所をサポートするモジュールを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、シンボルの別の場所をサポートするために、JustMyCode 状態を操作して、このインターフェイスを実装 (を参照してください、 [Visual Studio デバッガーの用語集](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)"JustMyCode"の定義で)。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)このインターフェイスを返します。 DE 送信、 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)インターフェイスを使用して、セッション デバッグ マネージャー (SDM) を[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)メソッドです。 呼び出しも、 [QueryInterface](/cpp/atl/queryinterface)上、 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)インターフェイスは、このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 メソッドだけでなく、 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)インターフェイス、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|シンボルとそれぞれのパスを検索した結果の検索パスの一覧を返します。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|ロードして、現在のモジュールのシンボルを初期化します。|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|返しますのモジュールがユーザー コードを表すかどうかを指定するフラグ。|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|見なすかどうか、モジュールがユーザー コードかどうかを指定します。|  
  
## <a name="remarks"></a>コメント  
 Visual Studio は、このインターフェイスの一般的な消費者です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)