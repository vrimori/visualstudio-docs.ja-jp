---
title: "CA1703: リソース文字列は正しく入力されなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ResourceStringsShouldBeSpelledCorrectly"
  - "CA1703"
helpviewer_keywords: 
  - "CA1703"
  - "ResourceStringsShouldBeSpelledCorrectly"
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1703: リソース文字列は正しく入力されなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|なし|  
  
## 原因  
 リソース文字列に Microsoft スペル チェック ライブラリで認識されない語が 1 つ以上含まれています。  
  
## 規則の説明  
 この規則では、リソース文字列を単語に分割し \(複合語のトークン化\)、個々の単語 \(トークン\) のスペルをチェックします。  解析アルゴリズムについては、「[CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)」を参照してください。  
  
 既定では、スペル チェック機能の英語 \(en\) バージョンが使用されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、正しいスペルの完全な単語を使用するか、違反とされた単語をカスタム辞書に追加します。  カスタム辞書を使用する方法については、「[CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)」を参照してください。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  正しいスペルの単語を使用すると、新しいソフトウェア ライブラリの習得に要する時間を短縮できます。  
  
## 関連規則  
 [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)  
  
 [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204: リテラルは正しく入力されていなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)