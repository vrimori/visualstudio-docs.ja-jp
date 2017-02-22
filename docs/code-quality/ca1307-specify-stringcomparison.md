---
title: "CA1307: StringComparison の指定 | Microsoft Docs"
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
  - "CA1307"
  - "SpecifyStringComparison"
helpviewer_keywords: 
  - "CA1307"
  - "SpecifyStringComparison"
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1307: StringComparison の指定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|CheckId|CA1307|  
|分類|Microsoft.Globalization|  
|互換性に影響する変更点|なし|  
  
## 原因  
 文字列比較演算で、<xref:System.StringComparison> パラメーターを設定しないメソッド オーバーロードが使用されています。  
  
## 規則の説明  
 多くの文字列演算 \(最も重要なものは <xref:System.String.Compare%2A> メソッドおよび <xref:System.String.Equals%2A> メソッド\) では、<xref:System.StringComparison> 列挙体をパラメーターとして受け取るオーバーロードが用意されています。  
  
 <xref:System.StringComparison> パラメーターを受け取るオーバーロードが存在する場合は、このパラメーターを受け取らないオーバーロードではなく、受け取るオーバーロードを使用する必要があります。  このパラメーターを明示的に設定すると、多くの場合、コードがわかりやすくなり、保守も簡単になります。  
  
## 違反の修正方法  
 この規則違反を修正するには、文字列比較メソッドを、<xref:System.StringComparison> 列挙体をパラメーターとして受け取るオーバーロードに変更します。  たとえば、`String.Compare(str1, str2)` を `String.Compare(str1, str2, StringComparison.Ordinal)` に変更します。  
  
## 警告を抑制する状況  
 ライブラリまたはアプリケーションが、限定されたローカル ユーザーを対象にしているためにローカライズされない場合は、この規則による警告を抑制しても安全です。  
  
## 参照  
 [グローバリゼーションの警告](../code-quality/globalization-warnings.md)   
 [CA1309: 順序を示す StringComparison を使用します](../code-quality/ca1309-use-ordinal-stringcomparison.md)