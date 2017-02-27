---
title: "CA1043: インデクサーには整数または文字列引数を使用します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
helpviewer_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1043: インデクサーには整数または文字列引数を使用します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseIntegralOrStringArgumentForIndexers|  
|CheckId|CA1043|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型またはプロテクト型に、<xref:System.Int32?displayProperty=fullName>、<xref:System.Int64?displayProperty=fullName>、<xref:System.Object?displayProperty=fullName>、または <xref:System.String?displayProperty=fullName> 以外のインデックス型を使用するパブリック インデクサーまたはプロテクト インデクサーが含まれます。  
  
## 規則の説明  
 インデクサー、言い換えるとインデックスされたプロパティでは、インデックスに整数型または文字列型を使用します。  一般に、このような型はデータ構造のインデックス作成に使用され、ライブラリの操作感も改善されます。  <xref:System.Object> 型の使用は、デザイン時に特定の整数型または文字列型を指定できない場合に限定してください。  デザインでインデックスにその他の型が必要な場合は、該当する型が論理的なデータ ストアを表しているかどうかを再確認します。  論理的なデータ ストアを表していない場合、メソッドを使用します。  
  
## 違反の修正方法  
 この規則違反を修正するには、インデックスを整数型または文字列型に変更するか、インデクサーではなくメソッドを使用するようにします。  
  
## 警告を抑制する状況  
 標準的ではないインデクサーの必要性を十分に考慮したうえで、この規則による警告を抑制します。  
  
## 使用例  
 <xref:System.Int32> インデックスを使用するインデクサーを次の例に示します。  
  
 [!CODE [FxCop.Design.IntegralOrStringIndexers#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers#1)]  
  
## 関連規則  
 [CA1023: インデクサーを多次元にすることはできません](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024: 適切な場所にプロパティを使用します](../code-quality/ca1024-use-properties-where-appropriate.md)