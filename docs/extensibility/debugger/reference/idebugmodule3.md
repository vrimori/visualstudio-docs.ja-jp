---
title: IDebugModule3 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b74063aa73db8258b2986ac1310d02e36027bf6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118454"
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
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)