---
title: "式の評価コンテキスト | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "式の評価、コンテキスト"
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 式の評価コンテキスト
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] で  **の式のコンテキスト** :  
  
-   式の評価のコンテキストを表します。  通常評価コンテキストとは変数パラメーター関数とメソッドを評価する構文のスコープに対応します。  たとえばスタック フレームに関連付けられた式の評価のコンテキストが評価のローカル変数メソッドのパラメーターおよびクラス メンバーのコンテキストを提供します \(該当する場合\)。  
  
-   プログラムがブレークポイントで停止したに存在します。  式自体は特定のコンテキスト内にバインドし評価の準備が整った解析された式を表すデータ構造です。  
  
     詳細に [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) の式はメソッドを使用して作成します。  式が評価されると印刷できる文字列を変数の名前と型引数と値を生成します。  この文字列はウォッチ ウィンドウや IDE の \[ローカル\] ウィンドウに表示されます。  
  
     `BSTR` と [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) のインターフェイスはデバッグ エンジンは式 \(DE\) を解析する [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) インターフェイスを作成できます。  `IDebugExpression2` のインターフェイスはde\-DE は同期または非同期式を評価して値を取得できます。  変数または引数の名前および型とともにこの値は表示のためにIDE に送信されます。  
  
## 参照  
 [式評価インターフェイス](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)