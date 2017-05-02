---
title: "&#39;return&#39; ステートメントが関数の外にあります。 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# &#39;return&#39; ステートメントが関数の外にあります。
コードのグローバル スコープで `return` ステートメントを使用しました。  `return` ステートメントは関数本体の内側のみで使用する必要があります。  
  
 関数に `()` 演算子を付けて呼び出すと、式として扱われます。  すべての式に値があり、関数の戻り値を `return` ステートメントで指定します。  一般的な書式は次のとおりです。  
  
```  
  
return [ expression ];  
```  
  
 `return` ステートメントを実行すると、*expression* が評価され、戻り値として返されます。  式が指定されていない場合は、**undefined** が返されます。  
  
 `return` ステートメントを実行すると、関数本体に他のステートメントが残っている場合でも関数は終了します。  ただし、**try** ブロック内にある **return** ステートメントを実行した場合で、対応する **finally** ブロックが記述されている場合は、**finally** ブロックのコードを実行してから関数が終了します。  
  
 `return` ステートメントを実行せずに関数本体の最後に到達して関数が終了した場合は、戻り値は **undefined** 値になります \(この場合、関数の結果をより大きい式の一部として使用することはできません\)。  
  
### このエラーを解決するには  
  
-   コードの本体 \(グローバル スコープ\) から `return` ステートメントを削除します。  
  
## 参照  
 [return ステートメント](../../javascript/reference/return-statement-javascript.md)   
 [Function オブジェクト](../../javascript/reference/function-object-javascript.md)   
 [caller プロパティ \(Function\)](../../javascript/reference/caller-property-function-javascript.md)