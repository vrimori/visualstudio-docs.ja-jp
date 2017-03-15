---
title: "CA1800: 不必要にキャストしません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1800"
  - "DoNotCastUnnecessarily"
helpviewer_keywords: 
  - "DoNotCastUnnecessarily"
  - "CA1800"
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1800: 不必要にキャストしません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotCastUnnecessarily|  
|CheckId|CA1800|  
|分類|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## 原因  
 メソッドで、引数またはローカル変数のいずれかについて二重のキャストを実行しました。  この規則違反を完全に解析するには、テスト対象のアセンブリをデバッグ情報を使用してビルドします。また、関連するプログラム データベース \(.pdb\) ファイルを使用できるようにします。  
  
## 規則の説明  
 二重のキャストがあるとパフォーマンスが低下します。特に、小さな繰り返しステートメントでキャストが実行される場合はそうです。  明示的に二重のキャストが必要な場合、二重にキャストするのではなく、ローカル変数にキャストの結果を格納し、ローカル変数を使用します。  
  
 実際のキャストを実行する前に、C\# の `is` 演算子を使用してキャストが成功するかどうかをテストしている場合、代わりに `as` 演算子の結果をテストすることをお勧めします。  こうすると、`is` 演算子によって暗黙的にキャストが実行されず、同じ機能を実現できます。  
  
## 違反の修正方法  
 この規則違反を修正するには、キャスト操作の数を最小限に抑えるようにメソッドの実装を変更します。  
  
## 警告を抑制する状況  
 パフォーマンスが重要ではない場合は、この規則による警告を抑制するか、この規則を完全に無視しても安全です。  
  
## 使用例  
 C\# の `is` 演算子を使用して、この規則に違反するメソッドを次の例に示します。  2 つ目のメソッドは、`is` 演算子を `as` 演算子の結果に対するテスト値で置き換えることで、この規則に適合しています。これによって、各繰り返しのキャスト操作の数が 2 つから 1 つに減ります。  
  
 [!code-cs[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]  
  
## 使用例  
 次の例では、複数の明示的なキャストが重複しているメソッド `start_Click` を示します。このメソッドは規則違反です。一方、メソッド `reset_Click` は、キャストをローカル変数に保持することで規則に適合しています。  
  
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-cs[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]  
  
## 参照  
 [as](/dotnet/csharp/language-reference/keywords/as)   
 [is](/dotnet/csharp/language-reference/keywords/is)