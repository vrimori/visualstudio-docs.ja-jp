---
title: "IDebugStackFrame2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2"
helpviewer_keywords: 
  - "IDebugStackFrame2 インターフェイス"
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは特定のスレッドのスタック フレームの呼び出しのスタックを表します。  
  
## 構文  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは \(DE\)スタック フレームを表すためこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) のインターフェイスを取得します [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)。  `IDebugStackFrame2` のインターフェイスを含む [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) の構造体を取得します [次へ](../Topic/IEnumDebugFrameInfo2::Next.md)。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugStackFrame2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)|このスタック フレームのコード コンテキストを取得します。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|このスタック フレームのドキュメントのコンテキストを取得します。|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|スタック フレームの名前を取得します。|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|スタック フレームの説明を取得します。|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|スタック フレームに関連付けられた物理アドレス範囲のコンピューターに依存しない表現を取得します。|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|スタック フレームとスレッドの現在のコンテキスト内での式を評価するためのコンテキストを取得します。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|言語のスタック フレームに関連付けられているを取得します。|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|スタック フレームに関連付けられたプロパティの説明を取得します。|  
|[EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)|スタック フレームのプロパティの列挙子を作成します。|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|スレッドのスタック フレームに関連付けられているを取得します。|  
  
## 解説  
 このインターフェイスはデバッグ対象がブレークポイントで停止した場合にのみ派生します \(ユーザー設定のブレークポイントまたは例外によってこと\)。  このインターフェイスで式を評価するために式のコンテキストを取得できますレジスタの一覧を返すことも呼び出し履歴はから派生して調べることができます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)