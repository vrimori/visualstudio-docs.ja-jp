---
title: "CA1055: URI 戻り値を文字列にすることはできません | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1055"
  - "UriReturnValuesShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1055"
  - "UriReturnValuesShouldNotBeStrings"
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1055: URI 戻り値を文字列にすることはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriReturnValuesShouldNotBeStrings|  
|CheckId|CA1055|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 メソッドの名前に "uri"、"Uri"、"urn"、"Urn"、"url"、または "Url" が含まれ、戻り値が文字列です。  
  
## 規則の説明  
 この規則では、メソッド名は Pascal 形式の大文字と小文字の表記規則に基づいて、トークンに分割されます。次に、各トークンは、"uri"、"Uri"、"urn"、"Urn"、"url"、または "Url" と一致するかどうかがチェックされます。  一致する場合、規則では、メソッドは URI \(Uniform Resource Identifier\) を返すと想定されます。  URI の文字列表現は解析エラーやエンコーディング エラーが発生しやすく、セキュリティ上の脆弱性の原因となる場合があります。  <xref:System.Uri?displayProperty=fullName> クラスを使用すると、安全な方法でこのサービスを実現できます。  
  
## 違反の修正方法  
 この規則違反を修正するには、戻り値の型を <xref:System.Uri> に変更します。  
  
## 警告を抑制する状況  
 戻り値が URI を表さない場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 この規則に違反している型 `ErrorProne` と、規則に適合する型 `SaferWay` を次の例に示します。  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]  
  
## 関連規則  
 [CA1056: URI プロパティを文字列にすることはできません](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: URI パラメーターを文字列にすることはできません](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA2234: 文字列の代わりに System.Uri オブジェクトを渡します](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1057: 文字列 URI オーバーロードが、System.Uri オーバーロードを呼び出します](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)