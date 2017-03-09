---
title: "CA1303: ローカライズされたパラメーターとしてリテラルを渡さないでください | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Do not pass literals as localized parameters"
  - "DoNotPassLiteralsAsLocalizedParameters"
  - "CA1303"
helpviewer_keywords: 
  - "CA1303"
  - "DoNotPassLiteralsAsLocalizedParameters"
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1303: ローカライズされたパラメーターとしてリテラルを渡さないでください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|分類|Microsoft.Globalization|  
|互換性に影響する変更点|なし|  
  
## 原因  
 メソッドが、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] クラス ライブラリのコンストラクターまたはメソッドへのパラメーターとして、リテラル文字列を渡しています。その文字列はローカライズできません。  
  
 この警告は、リテラル文字列が値としてパラメーターまたはプロパティに渡されており、次の条件の 1 つ以上に該当する場合に表示されます。  
  
-   パラメーターまたはプロパティの <xref:System.ComponentModel.LocalizableAttribute> 属性が true に設定されている。  
  
-   パラメーターまたはプロパティの名前に、"Text"、"Message"、または "Caption" という文字列が含まれている。  
  
-   Console.Write メソッドまたは Console.WriteLine メソッドに渡される文字列パラメーターの名前が、"value" または "format" である。  
  
## 規則の説明  
 ソース コードに埋め込まれているリテラル文字列は、ローカライズが困難です。  
  
## 違反の修正方法  
 この規則違反を修正するには、リテラル文字列を <xref:System.Resources.ResourceManager> クラスのインスタンスによって取得した文字列で置換します。  
  
## 警告を抑制する状況  
 コード ライブラリをローカライズしない場合、またはコード ライブラリを使用した文字列がエンド ユーザーまたは開発者に表示されない場合は、この規則による警告を抑制しても安全です。  
  
 こうすることで、ローカライズされた文字列を渡すことができないメソッドについて、ユーザーがノイズを除去できるようになります。除去するには、パラメーターまたはプロパティに付けられた名前を変更するか、これらの項目を条件付きにします。  
  
## 使用例  
 2 つの引数のいずれかが範囲外であるときに、例外をスローするメソッドを次の例に示します。  1 つ目の引数では、リテラル文字列が例外のコンストラクターに渡されるため、規則違反です。  2 つ目の引数では、<xref:System.Resources.ResourceManager> によって取得された文字列がコンストラクターに正しく渡されます。  
  
 [!CODE [FxCop.Globalization.DoNotPassLiterals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals#1)]  
  
## 参照  
 [デスクトップ アプリケーションのリソース](../Topic/Resources%20in%20Desktop%20Apps.md)