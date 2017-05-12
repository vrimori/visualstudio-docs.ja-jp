---
title: "IDebugStackFrame インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrame インターフェイス"
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame インターフェイス
スレッドのスタックの論理スタック フレームを表します。  式の評価、ウォッチ ウィンドウを使用する `IDebugExpressionContext` のインターフェイスを取得するに `IDebugStackFrame::QueryInterface` のメソッドを呼び出します。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugStackFrame` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|スタック フレームに関連付けられている現在のコンテキスト コードを返します。|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|スタック フレームの短い場合、長いテキストの説明を返します。|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|言語の短い場合、長いテキストの説明を返します。|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|このスタック フレームに関連付けられているスレッドを返します。|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|現在のフレームのプロパティ ブラウザーを返します。|