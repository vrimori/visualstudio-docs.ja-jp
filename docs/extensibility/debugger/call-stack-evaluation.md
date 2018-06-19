---
title: スタック評価を呼び出す |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bcfc2f2afa622534772390df59597f6972463de8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101304"
---
# <a name="call-stack-evaluation"></a>呼び出しスタックの評価
中断モード中に、呼び出し履歴のスタック フレームを表示するために実装する必要があります、 [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)メソッドです。  
  
## <a name="methods-for-evaluation"></a>評価のためのメソッド  
 単純なデバッグ エンジン (DE) には、1 つのみのスタック フレームが可能性があります。 中断モード中にスタック フレームを検証するには、次のメソッドを実装する必要があります[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)です。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|スタック フレームのコードのコンテキストを取得します。 コードのコンテキストでは、現在の命令ポインターのスタック フレームを表します。|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|スタック フレームのドキュメントのコンテキストを取得します。 ドキュメントのコンテキストでは、スタック フレームのソース コードの現在の場所を表します。 プログラムが停止したときに、ソース コードを表示するために必要です。|  
  
 これらのメソッドでは、いくつかのコンテキストに関連するインターフェイスとメソッドの実装が必要です。 したがって、実装する必要があります、 [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)メソッドと、次の方法の[IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)です。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|ドキュメントのコンテキストのファイルのステートメントの範囲を取得します。|  
  
 コードのコンテキストを列挙するには、すべてのメソッドを実装する必要があります[IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)です。  
  
## <a name="see-also"></a>関連項目  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)