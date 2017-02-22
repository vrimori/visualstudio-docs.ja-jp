---
title: "CA1804: 使用されていないローカルを削除します | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1804"
  - "RemoveUnusedLocals"
helpviewer_keywords: 
  - "RemoveUnusedLocals"
  - "CA1804"
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1804: 使用されていないローカルを削除します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveUnusedLocals|  
|CheckId|CA1804|  
|分類|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## 原因  
 メソッドでローカル変数を宣言していますが、その変数を使用していません。ただし、代入ステートメントの受け取りとして使用されている可能性はあります。  この規則違反を解析するには、テスト対象のアセンブリをデバッグ情報を含めてビルドします。また、関連するプログラム データベース \(.pdb\) ファイルを使用できるようにします。  
  
## 規則の説明  
 使用されていないローカル変数や不要な引数があると、アセンブリのサイズが大きくなり、パフォーマンスが低下します。  
  
## 違反の修正方法  
 この規則違反を修正するには、そのローカル変数を削除するか、使用します。  [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] に同梱される C\# コンパイラは、`optimize` オプションが有効である場合、このような未使用のローカル変数を削除します。  
  
## 警告を抑制する状況  
 そのローカル変数がコンパイラで生成された場合は、この規則による警告を抑制します。  また、パフォーマンスとコードの保守が重要ではない場合、この規則による警告を抑制するか、この規則を無効にしても安全です。  
  
## 使用例  
 使用されていないローカル変数を次の例にいくつか示します。  
  
 [!CODE [FxCop.Performance.UnusedLocals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals#1)]  
  
## 関連規則  
 [CA1809: ローカルを使用しすぎないでください](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811: 呼び出されていないプライベート コードを使用しません](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: インスタンス化されていない内部クラスを使用しないでください](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801: 使用されていないパラメーターを再確認します](../Topic/CA1801:%20Review%20unused%20parameters.md)