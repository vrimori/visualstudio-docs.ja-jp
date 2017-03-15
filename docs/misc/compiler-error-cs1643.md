---
title: "コンパイラ エラー CS1643 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1643"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1643"
ms.assetid: 521f352b-00fb-4d62-89be-44251db3cc5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1643
型 'type\!' のメソッドに値を返さないコード パスがあります  
  
 このエラーは、デリゲートの本体に return ステートメントが存在しない、または存在したとしても、その return ステートメントまで到達可能なことをコンパイラが確認できない場合に発生します。 次の例では、コンパイラは分岐条件の結果を予測することで、匿名メソッドのブロックから常に値が戻されるかどうかを検査しません。  
  
## 使用例  
 次の例では CS1643 が生成されます。  
  
```  
// CS1643.cs delegate int MyDelegate(); class C { static void Main() { MyDelegate d = delegate {                 // CS1643 int i = 0; if (i == 0) return 1; }; } }  
```