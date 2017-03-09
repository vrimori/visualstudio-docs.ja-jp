---
title: "これらの引数に最も固有な、アクセス可能な &#39;&lt;method&gt;&#39; がないため、オーバーロードの解決に失敗しました:&lt;error&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30521"
  - "vbc30521"
helpviewer_keywords: 
  - "解決エラー"
  - "BC30521"
  - "オーバーロードの解決に失敗しました"
ms.assetid: b8b41fa0-a64b-4e74-8443-be3afd2b6f11
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# これらの引数に最も固有な、アクセス可能な &#39;&lt;method&gt;&#39; がないため、オーバーロードの解決に失敗しました:&lt;error&gt;
オーバーロードされたメソッドを呼び出しましたが、引数リストを変換できるパラメーター リストを持つオーバーロードをコンパイラが 2 つ以上検出したため、そのうちの 1 つを選択できませんでした。  
  
 コンパイラは、呼び出し元の引数リスト内のデータ型と、オーバーロード パラメーター リスト内のデータ型をできるだけ一致させようとします。 型チェック スイッチ \([Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)\) が `On` であれ、あるいは `Off` であれ、引数それぞれから対応するパラメーターへの拡大変換が必要です。  
  
 コンパイラは、拡大要件を満たすオーバーロードを 2 つ以上検出すると、引数のデータ型に最も固有なオーバーロード、つまり必要な拡大量が最小のオーバーロードを探します。 1 つのオーバーロードが 1 つの引数のデータ型により固有で、もう 1 つのオーバーロードがもう 1 つの引数のデータ型により固有である場合、このエラー メッセージが生成されます。 使用例を含む詳細については、「[Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)」を参照してください。  
  
 **エラー ID:** BC30521  
  
### このエラーを解決するには  
  
1.  メソッドのすべてのオーバーロードを確認し、呼び出すものを決定します。  
  
2.  呼び出し元のステートメントで、引数のデータ型を目的のオーバーロード用に定義されたパラメーターのデータ型と一致させます。 1 つ以上のデータ型を定義された型に変換するには、[CType 関数](/dotnet/visual-basic/language-reference/functions/ctype-function) を使用する必要がある場合があります。  
  
## 参照  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Overloaded Properties and Methods](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [CType 関数](/dotnet/visual-basic/language-reference/functions/ctype-function)