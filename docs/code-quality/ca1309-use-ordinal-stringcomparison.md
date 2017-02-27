---
title: "CA1309: 順序を示す StringComparison を使用します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
helpviewer_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1309: 順序を示す StringComparison を使用します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOrdinalStringComparison|  
|CheckId|CA1309|  
|分類|Microsoft.Globalization|  
|互換性に影響する変更点|なし|  
  
## 原因  
 非言語的な文字列比較演算で、<xref:System.StringComparison> パラメーターが **Ordinal** または **OrdinalIgnoreCase** に設定されていません。  
  
## 規則の説明  
 多くの文字列演算 \(最も重要なものは <xref:System.String.Compare%2A?displayProperty=fullName> メソッドおよび <xref:System.String.Equals%2A?displayProperty=fullName> メソッド\) では、<xref:System.StringComparision?displayProperty=fullName> 列挙体をパラメーターとして受け取るオーバーロードが用意されました。  
  
 **StringComparison.Ordinal** または **StringComparison.OrdinalIgnoreCase** を指定すると、文字列比較は非言語的になります。  つまり、比較を判断する場合に、自然言語固有の機能は無視されます。  これは、判断は単純なバイト比較に基づいたものであることを示し、大文字と小文字の指定、またはカルチャでパラメーター化される同等の表は無視されます。  その結果、パラメーターを **StringComparison.Ordinal** または **StringComparison.OrdinalIgnoreCase** に明示的に設定することによって、多くの場合、コードの速度、正確さ、および信頼性が向上します。  
  
## 違反の修正方法  
 この規則違反を修正するには、文字列比較メソッドを、<xref:System.StringComparison?displayProperty=fullName> 列挙体をパラメーターとして受け取るオーバーロードに変更し、**Ordinal** または **OrdinalIgnoreCase** を指定します。  たとえば、`String.Compare(str1, str2)` を `String.Compare(str1, str2, StringComparison.Ordinal)` に変更します。  
  
## 警告を抑制する状況  
 ライブラリまたはアプリケーションが限定されたローカル ユーザーを想定している場合、または現在のカルチャのセマンティクスを使用する必要がある場合は、この規則による警告を抑制しても安全です。  
  
## 参照  
 [グローバリゼーションの警告](../code-quality/globalization-warnings.md)   
 [CA1307: StringComparison の指定](../code-quality/ca1307-specify-stringcomparison.md)