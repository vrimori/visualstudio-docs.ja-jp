---
title: "CA2204: リテラルは正しく入力されていなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Literals should be spelled correctly"
  - "CA2204"
  - "LiteralsShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA2204"
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2204: リテラルは正しく入力されていなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 メソッドはローカライズされた文字列を必要とするパラメーターまたはプロパティにリテラル文字列を渡しますが、そのリテラル文字列に、Microsoft スペル チェック ライブラリで認識されない単語が 1 つ以上含まれています。  
  
## 規則の説明  
 この規則では、次の条件に 1 つ以上に該当する場合に、値としてパラメーターまたはプロパティに渡されるリテラル文字列がチェックされます。  
  
-   パラメーターまたはプロパティの <xref:System.ComponentModel.LocalizableAttribute> 属性が true に設定されている。  
  
-   パラメーターまたはプロパティの名前に、"Text"、"Message"、または "Caption" という文字列が含まれている。  
  
-   Console.Write メソッドまたは Console.WriteLine メソッドに渡される文字列パラメーターの名前が、"value" または "format" である。  
  
 この規則では、リテラル文字列を複合語のトークン化によって単語に分割し、個々の単語 \(トークン\) のスペルをチェックします。  解析アルゴリズムについては、「[CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)」を参照してください。  
  
 既定では、スペル チェック機能の英語 \(en\) バージョンが使用されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、単語のスペルを修正するか、違反とされた単語をカスタム辞書に追加します。  カスタム辞書を使用する方法については、「[方法 : コード分析辞書をカスタマイズする](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)」を参照してください。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  正しいスペルの単語を使用すると、新しいソフトウェア ライブラリの習得に要する時間を短縮できます。  
  
## 関連規則  
 [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)