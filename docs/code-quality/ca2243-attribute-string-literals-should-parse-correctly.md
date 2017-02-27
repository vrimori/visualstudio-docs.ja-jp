---
title: "CA2243: 属性文字列リテラルは、正しく解析する必要があります | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2243"
  - "AttributeStringLiteralsShouldParseCorrectly"
helpviewer_keywords: 
  - "AttributeStringLiteralsShouldParseCorrectly"
  - "CA2243"
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# CA2243: 属性文字列リテラルは、正しく解析する必要があります
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AttributeStringLiteralsShouldParseCorrectly|  
|CheckId|CA2243|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 属性文字列のリテラル パラメーターが URL、GUID、またはバージョンとして正しく解析されません。  
  
## 規則の説明  
 属性は <xref:System.Attribute?displayProperty=fullName> から派生し、コンパイル時に使用されるため、コンストラクターには定数値だけを渡すことができます。  URL、GUID、およびバージョンを表す属性パラメーターは、<xref:System.Uri?displayProperty=fullName>、<xref:System.Guid?displayProperty=fullName>、および <xref:System.Version?displayProperty=fullName> として型指定することはできません。これらの型を定数として表すことはできないからです。  このような属性パラメーターは文字列で表す必要があります。  
  
 パラメーターを文字列として型指定することにより、コンパイル時に誤った形式のパラメーターが渡されることがあります。  
  
 この規則では、名前付けヒューリスティックを使用して、URI \(Uniform Resource Identifier\)、グローバル一意識別子 \(GUID\)、またはバージョンを表すパラメーターを検索し、渡された値が正しいことを確認します。  
  
## 違反の修正方法  
 パラメーター文字列を正しい形式の URL、GUID、またはバージョンに変更します。  
  
## 警告を抑制する状況  
 パラメーターが URL、GUID、またはバージョンを表さない場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 次の例は、この規則に違反する AssemblyFileVersionAttribute のコードを示しています。  
  
 [!code-cs[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 この規則は以下のパラメーターによってトリガーされます。  
  
-   “version” が含まれており、System.Version と解析できないパラメーター  
  
-   “guid” が含まれており、System.Guid と解析できないパラメーター  
  
-   “uri”、“urn”、または “url” が含まれており、System.Uri と解析できないパラメーター  
  
## 参照  
 [CA1054: URI パラメーターを文字列にすることはできません](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)