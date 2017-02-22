---
title: "CA1057: 文字列 URI オーバーロードが、System.Uri オーバーロードを呼び出します | Microsoft Docs"
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
  - "CA1057"
  - "StringUriOverloadsCallSystemUriOverloads"
helpviewer_keywords: 
  - "StringUriOverloadsCallSystemUriOverloads"
  - "CA1057"
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1057: 文字列 URI オーバーロードが、System.Uri オーバーロードを呼び出します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StringUriOverloadsCallSystemUriOverloads|  
|CheckId|CA1057|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 型でメソッドのオーバーロードを宣言していますが、文字列型のパラメーターを <xref:System.Uri?displayProperty=fullName> パラメーターで置き換えただけで他に違いがありません。また、文字列型のパラメーターを使用するオーバーロードが、<xref:System.Uri> パラメーターを使用するオーバーロードを呼び出していません。  
  
## 規則の説明  
 このオーバーロードは文字列型\/<xref:System.Uri> パラメーターのみが異なるため、文字列は URI \(Uniform Resource Identifier\) を表すと見なされます。  URI の文字列表現は解析エラーやエンコーディング エラーが発生しやすく、セキュリティ上の脆弱性の原因となる場合があります。  <xref:System.Uri> クラスを使用すると、安全な方法でこのサービスを実現できます。  <xref:System.Uri> クラスを活用するには、文字列のオーバーロードで、文字列型の引数を使用して <xref:System.Uri> のオーバーロードを呼び出します。  
  
## 違反の修正方法  
 URI の文字列表現を使用するメソッドを実装し直し、文字列型の引数を使用して <xref:System.Uri> クラスのインスタンスを作成します。次に、<xref:System.Uri> オブジェクトを、<xref:System.Uri> パラメーターを持つオーバーロードに渡します。  
  
## 警告を抑制する状況  
 文字列パラメーターが URI を表さない場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 適切に実装された文字列のオーバーロードの例を次に示します。  
  
 [!CODE [FxCop.Design.CallUriOverload#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload#1)]  
  
## 関連規則  
 [CA2234: 文字列の代わりに System.Uri オブジェクトを渡します](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1056: URI プロパティを文字列にすることはできません](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: URI パラメーターを文字列にすることはできません](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: URI 戻り値を文字列にすることはできません](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)