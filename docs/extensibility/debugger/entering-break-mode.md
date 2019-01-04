---
title: 中断モード |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f83059bb5608f99b9a984159771b5f37a1163ae
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53886177"
---
# <a name="enter-break-mode"></a>中断モードします。
次の情報には、関数にステップ インするか、カーソルが含まれる、ソース コードの行に実行するか、またはブレークポイントを実行している後にブレークポイントが発生したときに発生するプロセスについて説明します。  
  
## <a name="break-mode-process"></a>中断モードの処理  
  
1.  デバッグ エンジン (DE) 送信[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)、 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)、または中断モードに入る IDE が発生するその他の停止イベントです。  
  
2.  SDM は、次のように、スレッドから呼び出し履歴情報を取得します。  
  
    -   [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    -   [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    -   [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)ソース コード情報を取得するには  
  
    -   [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)ファイル名を取得するには  
  
    -   [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)ステートメントの範囲を取得するには  
  
    -   [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)メモリ情報を取得するには  
  
## <a name="see-also"></a>関連項目  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)