---
title: "[あいまいさの解決] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.Disambig"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "[あいまいさの解決] ダイアログ ボックス"
  - "デバッガー、[あいまいさの解決] ダイアログ ボックス"
  - "デバッグ [C++]、あいまいさの解決"
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# [あいまいさの解決] ダイアログ ボックス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[`Resolve Ambiguity`\] ダイアログ ボックスが表示されるのは、表示する場所をデバッガーが選択できない場合です。  たとえば、C\+\+ テンプレートを使用する場合は、単一の関数テンプレートから複数の関数を作成できます。  デバッガーがテンプレートのソースの場所で停止して、`Go To Disassembly` が選択されている場合、デバッガーには複数のオプションがあります。  テンプレートから作成された各関数は独自の逆アセンブリ コードを持っており、デバッガーはどのコードを表示するのかを認識していません。  \[`Resolve Ambiguity`\] ダイアログ ボックスでは、対応するすべての場所の一覧から目的の場所を選択できます。  
  
 `Choose the specific location`  
 コマンドに対応するすべての場所の一覧を表示します。  
  
 `Address`  
 各関数のメモリ アドレスを表示します。  
  
 `Function`  
 各関数の名前を表示します。  
  
 `Module`  
 関数のオブジェクト コードを含むモジュール \(EXE または DLL\) を表示します。  
  
## 参照  
 [デバッガー内の式](../debugger/expressions-in-the-debugger.md)