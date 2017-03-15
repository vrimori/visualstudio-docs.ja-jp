---
title: "CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
helpviewer_keywords: 
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり – アセンブリで発生した場合。<br /><br /> なし – 型パラメーター上で発生した場合。|  
  
## 原因  
 識別子の名前に複数の語が含まれており、大文字と小文字が正しく使い分けられていない複合語が 1 つ以上あります。  
  
## 規則の説明  
 識別子の名前は大文字と小文字に基づく単語に分割されます。  Microsoft のスペル チェック ライブラリは、連続する 2 つの単語をチェックします。  それが認識されると、その識別子はこの規則への違反となります。  違反となる複合語の例として、"CheckSum" や "MultiPart" があります。それぞれの正しい表記は、"Checksum" および "Multipart" です。  以前は広く使用されていたことから、この規則にはいくつかの例外が含まれており、単一の語でありながら 2 つの語となるように大文字と小文字を使い分ける必要がある場合もあります \(この場合は "ToolBar" と "FileName"\)。  
  
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。  これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージ コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
## 違反の修正方法  
 名前の大文字と小文字を正しく記述します。  
  
## 警告を抑制する状況  
 複合語を構成する 2 つの語がいずれもスペル チェック用の辞書によって認識され、その 2 つの語を意図的に使用する場合は、この規則による警告を抑制しても安全です。  
  
## 関連規則  
 [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)  
  
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## 参照  
 [名前付けのガイドライン](../Topic/Naming%20Guidelines.md)   
 [大文字と小文字の表記規則](../Topic/Capitalization%20Conventions.md)