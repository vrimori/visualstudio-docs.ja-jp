---
title: "CA1056: URI プロパティを文字列にすることはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UriPropertiesShouldNotBeStrings"
  - "CA1056"
helpviewer_keywords: 
  - "CA1056"
  - "UriPropertiesShouldNotBeStrings"
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA1056: URI プロパティを文字列にすることはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriPropertiesShouldNotBeStrings|  
|CheckId|CA1056|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 型で、名前に "uri"、"Uri"、"urn"、"Urn"、"url"、または "Url" を含む文字列のプロパティを宣言しています。  
  
## 規則の説明  
 この規則では、プロパティ名は Pascal 形式の大文字と小文字の表記規則に基づいて、トークンに分割されます。次に、各トークンは、"uri"、"Uri"、"urn"、"Urn"、"url"、または "Url" と一致するかどうかがチェックされます。  一致する場合、規則では、プロパティは URI \(Uniform Resource Identifier\) を表すと想定されます。  URI の文字列表現は解析エラーやエンコーディング エラーが発生しやすく、セキュリティ上の脆弱性の原因となる場合があります。  <xref:System.Uri?displayProperty=fullName> クラスを使用すると、安全な方法でこのサービスを実現できます。  
  
## 違反の修正方法  
 この規則違反を修正するには、プロパティを <xref:System.Uri> 型に変更します。  
  
## 警告を抑制する状況  
 プロパティが URI を表さない場合は、この規則に基づく警告を抑制しても安全です。  
  
## 使用例  
 この規則に違反している型 `ErrorProne` と、規則に適合する型 `SaferWay` を次の例に示します。  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]  
  
## 関連規則  
 [CA1054: URI パラメーターを文字列にすることはできません](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: URI 戻り値を文字列にすることはできません](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: 文字列の代わりに System.Uri オブジェクトを渡します](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1057: 文字列 URI オーバーロードが、System.Uri オーバーロードを呼び出します](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)