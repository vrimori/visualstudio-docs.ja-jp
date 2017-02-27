---
title: "CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldBeCasedCorrectly"
  - "CA1709"
helpviewer_keywords: 
  - "CA1709"
  - "IdentifiersShouldBeCasedCorrectly"
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 29
---
# CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり – アセンブリ、名前空間、型、メンバー、およびパラメーターで発生した場合。<br /><br /> なし – ジェネリック型パラメーターで発生した場合。|  
  
## 原因  
 識別子名の大文字と小文字が正しく使い分けられていません。  
  
 または  
  
 識別子の名前に 2 文字の頭字語が含まれ、2 文字目が小文字です。  
  
 または  
  
 識別子の名前に、3 字以上の英大文字の頭字語が含まれます。  
  
## 規則の説明  
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。  これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージ コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
 規則では、パラメーター名では Camel 形式を使用します。名前空間、型、およびメンバーの各名前では Pascal 形式を使用します。  Camel 形式の名前では、先頭文字は小文字にし、名前に含まれる残りの単語の先頭文字は大文字にします。  たとえば、Camel 形式で名前を表記すると、"packetSniffer"、"ioFile"、"fatalErrorCode" のようになります。  Pascal 形式の名前では、先頭文字は大文字にし、名前に含まれる残りの単語の先頭文字も大文字にします。  たとえば、Pascal 形式で名前を表記すると、"PacketSniffer"、"IOFile"、"FatalErrorCode" のようになります。  
  
 この規則では、大文字と小文字に基づいて名前を単語に分割し、任意の 2 文字の単語を、一般的な 2 文字の英単語 \("In" や "My" など\) のリストと照合します。  一致が検出されない場合、その単語は頭字語と扱われます。  また、この規則では、英大文字が 4 字連続している場合、または英大文字が名前の末尾で 3 字連続している場合に、名前を頭字語と見なします。  
  
 名前付け規則に従うと、2 字の頭字語ではすべて英大文字を使用し、3 字以上の頭字語は Pascal 形式の表記方法を使用します。  この名前付け規則を使用した例は、"DB"、"CR"、"Cpa"、および "Ecma" です。  この規則に違反する例は、"Io"、"XML"、および "DoD" です。パラメーター名以外の場合、"xp" と "cpl" も違反しています。  
  
 "ID" でこの規則違反が発生するのは、特殊な例です。「ID」は頭字語ではありませんが、「identifier」の省略形です。  
  
## 違反の修正方法  
 名前の大文字と小文字を正しく記述します。  
  
## 警告を抑制する状況  
 独自の名前付け規則がある場合、または識別子が正しい名前 \(会社名、テクノロジ名など\) を表している場合は、この警告を抑制しても安全です。  
  
 コード分析カスタム辞書に特定の用語、省略形、および頭字語を追加することもできます。  カスタム辞書で指定されている用語はこの規則の違反の原因になりません。  詳細については、「[方法 : コード分析辞書をカスタマイズする](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)」を参照してください。  
  
## 関連規則  
 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)