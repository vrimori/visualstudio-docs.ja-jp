---
title: "CA1054: URI パラメーターを文字列にすることはできません | Microsoft Docs"
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
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1054: URI パラメーターを文字列にすることはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriParametersShouldNotBeStrings|  
|CheckId|CA1054|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 型で、"uri"、"Uri"、"urn"、"Urn"、"url"、または "Url" という文字列パラメーターを持つメソッドを宣言しています。また、その型では、<xref:System.Uri?displayProperty=fullName> パラメーターを使用する、対応するオーバーロードを宣言していません。  
  
## 規則の説明  
 この規則では、パラメーター名は Camel 形式の大文字と小文字の表記規則に基づいて、トークンに分割されます。次に、各トークンは、"uri"、"Uri"、"urn"、"Urn"、"url"、または "Url" と一致するかどうかがチェックされます。  一致する場合、規則では、パラメーターは URI \(Uniform Resource Identifier\) を表すと想定されます。  URI の文字列表現は解析エラーやエンコーディング エラーが発生しやすく、セキュリティ上の脆弱性の原因となる場合があります。  メソッドで URI の文字列形式を使用する場合、対応するオーバーロードを宣言し、<xref:System.Uri> クラスのインスタンスを使用します。こうすることで、安全な方法でこのサービスを実現できます。  
  
## 違反の修正方法  
 この規則違反を修正するには、パラメーターを <xref:System.Uri> 型に変更します。これは互換性に影響のある変更です。  代替案として、<xref:System.Uri> パラメーターを使用するメソッドのオーバーロードを宣言する方法もあります。これは互換性に影響がありません。  
  
## 警告を抑制する状況  
 パラメーターが URI を表さない場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 この規則に違反している型 `ErrorProne` と、規則に適合する型 `SaferWay` を次の例に示します。  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]  
  
## 関連規則  
 [CA1056: URI プロパティを文字列にすることはできません](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1055: URI 戻り値を文字列にすることはできません](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: 文字列の代わりに System.Uri オブジェクトを渡します](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1057: 文字列 URI オーバーロードが、System.Uri オーバーロードを呼び出します](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)