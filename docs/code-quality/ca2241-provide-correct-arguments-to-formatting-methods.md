---
title: "CA2241: 正しい引数を書式指定メソッドに指定します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2241"
  - "Provide correct arguments to formatting methods"
  - "ProvideCorrectArgumentsToFormattingMethods"
helpviewer_keywords: 
  - "CA2241"
  - "ProvideCorrectArgumentsToFormattingMethods"
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA2241: 正しい引数を書式指定メソッドに指定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideCorrectArgumentsToFormattingMethods|  
|CheckId|CA2241|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 <xref:System.Console.WriteLine%2A>、<xref:System.Console.Write%2A>、<xref:System.String.Format%2A?displayProperty=fullName> などのメソッドに渡される `format` 文字列引数に、各オブジェクトの引数に対応する書式指定項目が含まれていません \(その逆も考えられます\)。  
  
## 規則の説明  
 <xref:System.Console.WriteLine%2A>、<xref:System.Console.Write%2A>、および <xref:System.String.Format%2A> などのメソッドに対する引数は、書式指定文字列と、それに続くいくつかの <xref:System.Object?displayProperty=fullName> インスタンスで構成されます。  書式指定文字列は、テキストと、{index\[,alignment\]\[:formatString\]} という形式の埋め込みの書式指定項目で構成されます。「インデックスは形式にオブジェクトを示すインデックス番号が 0 から始まるの整数です。  オブジェクトに、書式指定文字列の対応インデックスがない場合、そのオブジェクトは無視されます。  "index" で指定されたオブジェクトが存在しない場合、実行時に <xref:System.FormatException?displayProperty=fullName> がスローされます。  
  
## 違反の修正方法  
 この規則違反を修正するには、各オブジェクトの引数に書式指定項目を指定し、各書式指定項目にオブジェクト引数を指定します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則の 2 つの違反例を次に示します。  
  
 [!CODE [FxCop.Usage.FormattingArguments#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments#1)]