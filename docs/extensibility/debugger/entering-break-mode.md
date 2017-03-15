---
title: "中断モード | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "中断モード"
  - "[デバッグの SDK] のデバッグ、中断モード"
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 中断モード
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次はプロセスを示しブレークポイントを関数についての後に来る場合カーソルを実行しまたはで発生するソース・コード行ブレークポイントまで実行します。  
  
## 中断モードの手順  
  
1.  デバッグ エンジンにより \(DE\) [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) もIDE は中断モードになりますが他の停止のイベントが送信します。  
  
2.  SDM はスレッドから次のように呼び出し履歴情報を取得します :  
  
    -   [IDebugThread2:: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2:: GetCount](../Topic/IEnumDebugFrameInfo2::GetCount.md)  
  
    -   [IEnumDebugFrameInfo2:: 次へ](../Topic/IEnumDebugFrameInfo2::Next.md)  
  
    -   ソース・コードの情報を取得する [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)  
  
    -   ファイル名を取得 [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)  
  
    -   ステートメントのスコープを取得 [IDebugDocumentContext2:: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)  
  
    -   メモリ情報を取得する [IDebugStackFrame2:: GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)  
  
## 参照  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)