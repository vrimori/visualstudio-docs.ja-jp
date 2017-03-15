---
title: "CA1715: 識別子は正しいプレフィックスを含んでいなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1715"
  - "IdentifiersShouldHaveCorrectPrefix"
helpviewer_keywords: 
  - "IdentifiersShouldHaveCorrectPrefix"
  - "CA1715"
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# CA1715: 識別子は正しいプレフィックスを含んでいなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectPrefix|  
|CheckId|CA1715|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり – インターフェイスで発生した場合。<br /><br /> なし – ジェネリック型パラメーターで発生した場合。|  
  
## 原因  
 外部から参照できるインターフェイスの名前が大文字の "I" から始まっていません。  
  
 または  
  
 外部から参照できる型またはメソッドのジェネリック型パラメーターの名前が、大文字の "T" から始まっていません。  
  
## 規則の説明  
 規則では、特定のプログラミング要素名は、固有のプレフィックスで始まります。  
  
 インターフェイス名は、大文字の "I" で始め、別の英大文字を続けます。  この規則では、"MyInterface" と "IsolatedInterface" などのインターフェイス名の場合に違反をレポートします。  
  
 ジェネリック型パラメーターの名前は、大文字の "T" で始め、必要に応じて別の英大文字を続けます。  この規則では、"V" や "Type" などのジェネリック型パラメーター名の場合に違反をレポートします。  
  
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。  これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージ コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
## 違反の修正方法  
 識別子のプレフィックスが正しくなるように名前を変更します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 **次の例に、不適切な名前のインターフェイスを示します。**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]  
  
## 使用例  
 **インターフェイス名の先頭に "T" を付けることによって上記の違反を修正するコード例を次に示します。**  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]  
  
## 使用例  
 **次の例に、不適切な名前のジェネリック型パラメーターを示します。**  
  
 [!CODE [FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1)]  
  
## 使用例  
 **ジェネリック型パラメーター名の先頭に "T" を付けることによって上記の違反を修正するコード例を次に示します。**  
  
 [!CODE [FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1)]  
  
## 関連規則  
 [CA1722: 識別子は不適切なプレフィックスを含むことはできません。](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)