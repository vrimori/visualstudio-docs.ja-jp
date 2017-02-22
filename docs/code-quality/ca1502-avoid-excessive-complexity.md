---
title: "CA1502: メソッドの実装を複雑にしすぎないでください | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveComplexity"
  - "CA1502"
helpviewer_keywords: 
  - "CA1502"
  - "AvoidExcessiveComplexity"
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1502: メソッドの実装を複雑にしすぎないでください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveComplexity|  
|CheckId|CA1502|  
|分類|Microsoft.Maintainability|  
|互換性に影響する変更点|なし|  
  
## 原因  
 メソッドのサイクロマティック複雑度が高すぎます。  
  
## 規則の説明  
 *サイクロマティック複雑度*は、線形独立のメソッド経路数を示す尺度で、条件分岐の数と複雑さによって決まります。  メソッドのサイクロマティック複雑度が低い場合、一般に、理解、テスト、保守が容易であることを示します。  サイクロマティック複雑度は、メソッドの制御フロー グラフから次のように算出されます。  
  
 サイクロマティック複雑度 \= "edge" の数 \- "node" の数 \+ 1  
  
 ここで、"node" は論理的な分岐ポイントを表し、"edge" はノード間のラインを表します。  
  
 サイクロマティック複雑度が 25 を超えると、この規則違反がレポートされます。  
  
 [マネージ コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)でコード メトリックスの詳細について学習できます。  
  
## 違反の修正方法  
 この規則違反を修正するには、メソッドをリファクタリングし、サイクロマティック複雑度を減らします。  
  
## 警告を抑制する状況  
 複雑度を簡単に低下できず、そのメソッドの理解、テスト、および保守が容易である場合、この規則による警告を抑制しても安全です。  特に、大規模な `switch` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では `Select`\) ステートメントを含むメソッドは、除外できる場合がよくあります。  開発サイクルの後期にコード ベースが不安定になるリスク、または以前にリリース済みのコードで実行時の動作に予期しない変化が発生するリスクが、コードをリファクタリングすることで得られる保守性の利点よりも重大なこともあります。  
  
## サイクロマティック複雑度の算出方法  
 サイクロマティック複雑度は、以下のものに 1 を加算して算出されます。  
  
-   分岐 \(`if`、`while`、および `do` など\) の数  
  
-   `switch` 内の `case` ステートメントの数。  
  
 さまざまなサイクロマティック複雑度のメソッドを次の例に示します。  
  
## 使用例  
 **サイクロマティック複雑度 1**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## 使用例  
 **サイクロマティック複雑度 2**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## 使用例  
 **サイクロマティック複雑度 3**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## 使用例  
 **サイクロマティック複雑度 8**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## 関連規則  
 [CA1501: 継承を使用しすぎないでください](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## 参照  
 [マネージ コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)