---
title: 呼び出しスタックの評価 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 53c091503a48129466f705774061e1beb391f1a7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002822"
---
# <a name="call-stack-evaluation"></a>呼び出しスタックの評価
中断モード中に、コール スタックのスタック フレームを表示するために実装する必要があります、 [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)メソッド。  
  
## <a name="methods-for-evaluation"></a>評価のためのメソッド  
 単純なデバッグ エンジン (DE)、スタック フレームを 1 つだけあります。 中断モード中にスタック フレームを検証するには、次のメソッドを実装する必要があります[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|スタック フレームのコードのコンテキストを取得します。 コードのコンテキストでは、スタック フレーム内の現在の命令ポインターを表します。|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|スタック フレームのドキュメント コンテキストを取得します。 ドキュメントのコンテキストでは、スタック フレームのソース コードの現在の場所を表します。 プログラムが停止したときに、ソース コードを表示するために必要です。|  
  
 これらのメソッドでは、いくつかのコンテキストに関連するインターフェイスおよびメソッドの実装が必要です。 したがって、実装する必要があります、 [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)メソッドと次のメソッドの[IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|ドキュメント コンテキストのファイルのステートメントの範囲を取得します。|  
  
 コード コンテキストを列挙するには、すべてのメソッドを実装する必要があります[IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)します。  
  
## <a name="see-also"></a>関連項目  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)