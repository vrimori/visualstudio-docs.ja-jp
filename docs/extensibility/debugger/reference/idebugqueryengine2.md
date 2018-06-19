---
title: IDebugQueryEngine2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 402fc37d2ee78d834a2a88d070277c7b90ac3ecb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122744"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
このインターフェイスにより、デバッグ マネージャー (SDM) をデバッグ エンジン (DE) を表すインターフェイスを取得するセッションです。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 DE、最も一般的な DE インターフェイスを実装するオブジェクトに対してこのインターフェイスを実装する (など[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)、 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)、および[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) でアクセスを許可する順序、 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) DE 自体のインターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[QueryInterface](/cpp/atl/queryinterface)をこのインターフェイスを取得する代表的な DE インターフェイスにします。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugQueryEngine2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|カスタム デバッグ エンジン (DE) インターフェイスを取得します。|  
  
## <a name="remarks"></a>コメント  
 通常、このインターフェイスを実装するオブジェクトで実装、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス関数をステップ実行因果関係の順序付けですつまり、デバッガーがステップ実行関数の場合、外の場合をサポートするために、。次の関数を実行可能性がありますいないスタックで前の関数が別のスレッド内の関数を完全にあります。 「因果関係の作成」の定義では、次を参照してください。、 [Visual Studio デバッガーの用語集](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)