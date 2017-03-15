---
title: "呼び出しスタックの評価 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] 呼び出しスタックの評価のデバッグ"
  - "呼び出し履歴、評価版"
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# 呼び出しスタックの評価
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

中断モードでは呼び出し履歴のスタック フレームを表示するには[EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) のメソッドを実装する必要があります。  
  
## 評価のメソッド  
 単純なデバッグ エンジン \(DE\) では1 種類のスタック フレームである場合があります。  中断モード時にスタック フレームを確認するには[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) の次のメソッドを実装する必要があります。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)|スタック フレームのコード コンテキストを取得します。  コード コンテキストにはスタック フレームの現在の命令ポインターを表します。|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|スタック フレームのドキュメントのコンテキストを取得します。  ドキュメントのコンテキストスタック フレームのソース・コードの現在位置を表します。  プログラムで停止するときにソース・コードを表示する場合に必要です。|  
  
 これらのメソッドは複数のコンテキストに関連するインターフェイスおよびメソッドの実装が必要です。  したがって[IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) の [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md) の次のメソッドとメソッドを実装する必要があります。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|ドキュメントのコンテキストのファイルのステートメントの範囲を取得します。|  
  
 コード コンテキストを列挙するには[IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) のすべてのメソッドを実装する必要があります。  
  
## 参照  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)