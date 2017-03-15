---
title: "CA1700: enum 値に &#39;Reserved&#39; という名前を指定しません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1700"
  - "DoNotNameEnumValuesReserved"
helpviewer_keywords: 
  - "DoNotNameEnumValuesReserved"
  - "CA1700"
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1700: enum 値に &#39;Reserved&#39; という名前を指定しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotNameEnumValuesReserved|  
|CheckId|CA1700|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## 原因  
 列挙体のメンバー名に、"reserved" という単語が含まれています。  
  
## 規則の説明  
 この規則では、"reserved" を含む名前の列挙体のメンバーは、現在使用されていなくても、将来的なバージョンでは名前を変更するか削除されるプレースホルダーと想定しています。  メンバーの名前変更や削除は、互換性に影響する変更点です。  "reserved" が含まれる名前であるという理由だけで、ユーザーがメンバーを無視するとは限りません。また、ユーザーがドキュメントを読んだり内容に従うことも期待できません。  さらに、予約済みのメンバーもオブジェクト ブラウザーと高機能の統合開発環境に表示されるため、実際に使用されているメンバーがわかりづらくなります。  
  
 将来的なバージョンでは、予約済みのメンバーを使用するのではなく、列挙体に新しいメンバーを追加します。  ほとんどの場合、新しいメンバーの追加によって元のメンバー値が変化しなければ、互換性に影響はありません。  
  
 元のメンバーで元の値を保持している場合でもメンバーの追加によって互換性に影響が及ぶ状況は限られています。  第 1 に、既存のコード パスから新しいメンバーを返すことはできません。新しいメンバーを返すには、互換性に影響のある呼び出し元が、メンバー リスト全体を網羅する戻り値で `switch` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では `Select`\) ステートメントを使用する方法と、既定のときに例外をスローする方法があります。  第 2 に、クライアント コードでは、<xref:System.Enum.IsDefined%2A?displayProperty=fullName> などのリフレクション メソッドによる動作が変化したときに処理できない問題が考えられます。  したがって、既存のメソッドから新しいメンバーを返す必要がある場合、またはリフレクションの不適切な使用方法に起因するアプリケーション互換性問題がある場合、互換性に影響を及ぼさない唯一のソリューションは次のようになります。  
  
1.  元のメンバーと新しいメンバーを含む新しい列挙体を追加します。  
  
2.  元の列挙体に <xref:System.ObsoleteAttribute?displayProperty=fullName> 属性でマークします。  
  
 このとき、外部から参照できる型または元の列挙体を公開するメンバーの場合と同じ手順に従います。  
  
## 違反の修正方法  
 この規則違反を修正するには、メンバーを削除するか名前を変更します。  
  
## 警告を抑制する状況  
 現在使用されているメンバーや以前にリリース済みのライブラリに対してこの規則による警告を抑制しても安全です。  
  
## 関連規則  
 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1712: enum 値を型名のプレフィックスにしません](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: 列挙ストレージは Int32 でなければなりません](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1008: Enums は 0 値を含んでいなければなりません](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)