---
title: IDebugQueryEngine2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f80e8b44326cb082c8f6428365bad2575c317da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536233"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugQueryEngine2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugqueryengine2)します。  
  
このインターフェイスには、セッション デバッグ マネージャー (SDM) デバッグ エンジン (DE) を表すインターフェイスを取得することができます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 DE、最も一般的な DE インターフェイスを実装するオブジェクトのこのインターフェイスを実装する (など[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)、 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)、および[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) でアクセスを許可する順序、 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) DE 自体のインターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)でこのインターフェイスを取得するための一般的な DE インターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugQueryEngine2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|カスタム デバッグ エンジン (DE) のインターフェイスを取得します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスは、通常を実装するオブジェクトの実装、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス関数をステップ実行因果関係の順序付けられているつまり、関数から、デバッガーがステップ実行をサポートするために、。次の関数を実行できない可能性があります、スタックで、前の関数が別のスレッド内の関数全体。 「因果関係」の定義では、次を参照してください。、 [Visual Studio デバッガーの用語集](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)します。  
  
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

