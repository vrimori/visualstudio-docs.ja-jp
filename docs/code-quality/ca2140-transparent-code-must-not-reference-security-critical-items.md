---
title: "CA2140: 透過的コードは、セキュリティ上重要な項目を参照してはならない | Microsoft Docs"
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
  - "CA2129"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
  - "CA2140"
helpviewer_keywords: 
  - "CA2129"
  - "CA2140"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2140: 透過的コードは、セキュリティ上重要な項目を参照してはならない
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|  
|CheckId|CA2140|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 次のような透過的なメソッドです。  
  
-   セキュリティ上重要なセキュリティ例外型を処理する。  
  
-   セキュリティ上重要な型としてマークされたパラメーターを持つ。  
  
-   セキュリティ上重要な制約が指定されたジェネリック パラメーターを持つ。  
  
-   セキュリティ上重要な型のローカル変数を持つ。  
  
-   セキュリティ上重要としてマークされたデータ型を参照する。  
  
-   セキュリティ上重要としてマークされたメソッドを呼び出す。  
  
-   セキュリティ上重要としてマークされたフィールドを参照する。  
  
-   セキュリティ上重要としてマークされたデータ型を返す。  
  
## 規則の説明  
 <xref:System.Security.SecurityCriticalAttribute> 属性が適用されたコード要素は、セキュリティ上重要になります。  透過的なメソッドでセキュリティ上重要な要素を使用することはできません。  透過データ型でセキュリティ上重要な型を使用しようとすると、<xref:System.TypeAccessException>、<xref:System.MethodAccessException>、<xref:System.FieldAccessException> のいずれかの例外が発生します。  
  
## 違反の修正方法  
 この規則違反を修正するには、次のいずれかの処理を実行します。  
  
-   セキュリティ上重要なコードを使用するコード要素に <xref:System.Security.SecurityCriticalAttribute> 属性を適用する。  
  
     または  
  
-   セキュリティ上重要としてマークされているコード要素から <xref:System.Security.SecurityCriticalAttribute> 属性を削除し、<xref:System.Security.SecuritySafeCriticalAttribute> 属性または <xref:System.Security.SecurityTransparentAttribute> 属性を適用する。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 次の例では、セキュリティ上重要なジェネリック コレクション、フィールド、およびメソッドを、透過的なメソッドで参照しています。  
  
 [!code-cs[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## 参照  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>