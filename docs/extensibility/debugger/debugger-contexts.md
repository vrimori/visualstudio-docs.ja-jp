---
title: "デバッガー コンテキスト | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] コンテキストのデバッグ"
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# デバッガー コンテキスト
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ではデバッグ エンジンは \(DE\)個別のコンテキスト内で次のように同時に実行されます :  
  
-   プログラム実行ストリーム内の現在の位置を表すコード コンテキスト。  
  
-   ソース ドキュメント内の現在位置を記述する場所またはドキュメントのコンテキスト。  
  
-   式の評価がのコンテキストを記述する式の評価のコンテキスト。  
  
## このセクションの内容  
 [コード コンテキスト](../../extensibility/debugger/code-context.md)  
 現在のランタイム アーキテクチャでプログラム命令ストリームでアドレスとしてコード コンテキストとコードが命令によって表されるそのほかの手段ついて説明します。従来とは異なり言語。  
  
 [ドキュメントの場所](../../extensibility/debugger/document-position.md)  
 IDE で認識されるようにソース ファイルの場所の抽象化して Visual Studio のデバッグに関連するドキュメントの場所を定義します。  
  
 [ドキュメントのコンテキスト](../../extensibility/debugger/document-context.md)  
 どのドキュメントのコンテキストはソース ファイルに関連する Visual Studio のデバッグで表すかについて説明します。  またシンボル ハンドラーがドキュメントのコンテキストにコード コンテキストをどのようにマップするかについて説明します。  
  
 [式の評価のコンテキスト](../../extensibility/debugger/expression-evaluation-context.md)  
 Visual Studio の式の評価のコンテキストについて説明します。  たとえばスタック フレームに関連付けられた式の評価のコンテキストが評価のローカル変数メソッドのパラメーターおよびクラス メンバーのコンテキストを用意します。  
  
## 関連項目  
 [デバッグの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグの主要なアーキテクチャの概念について説明します。  
  
 [デバッグ コンポーネント](../../extensibility/debugger/debugger-components.md)  
 デバッグ エンジン \(DE\)式エバリュエーターとシンボル ハンドラーを含む Visual Studio のデバッグ コンポーネントの \(EE\) 概要を説明します。\(SH\)  
  
 [デバッグ タスク](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動し式を評価などのさまざまなデバッグ タスクへのリンクが含まれます。