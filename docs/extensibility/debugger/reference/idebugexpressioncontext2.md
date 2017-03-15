---
title: "IDebugExpressionContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionContext2"
helpviewer_keywords: 
  - "IDebugExpressionContext2 インターフェイス"
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは式の評価のコンテキストを表します。  
  
## 構文  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは \(DE\)式を評価できるコンテキストを表すためこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) の呼び出しはこのインターフェイスを返します。  このインターフェイスはプログラムのデバッグを停止スタック フレームが使用できる場合にのみアクセスできます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugExpressionContext2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetName](../Topic/IDebugExpressionContext2::GetName.md)|評価コンテキストの名前を取得します。|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|評価のテキスト ベースの式を解析します。|  
  
## 解説  
 コンテキストは評価式の評価を実行するための範囲と考えることができます。  
  
 プログラムが終了するとデバッグ セッション マネージャーは \(SDM\) を呼び出してからします [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) にスタック フレームを取得します。  SDM は`IDebugExpressionContext2` のインターフェイスを取得するに [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) を呼び出します。  これは [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) の呼び出しに評価できる状態となります。解析された式を表す [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) のインターフェイスを作成するように指定します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)