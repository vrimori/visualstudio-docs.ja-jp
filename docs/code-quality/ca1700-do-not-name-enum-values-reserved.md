---
title: "Ca 1700: いない名前列挙型値 &#39;予約済み (& m); #39 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2acfafaec213f619dbe8c3077ab5cc72bdfde88d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>Ca 1700: いない名前列挙型値 &#39;予約済み (& a) #39 です。
|||  
|-|-|  
|TypeName|DoNotNameEnumValuesReserved|  
|CheckId|CA1700|  
|カテゴリ|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 列挙体のメンバーの名前には、「予約済み"という単語にはが含まれています。  
  
## <a name="rule-description"></a>規則の説明  
 この規則では、"reserved" を含む名前の列挙体のメンバーは、現在使用されていなくても、将来的なバージョンでは名前を変更するか削除されるプレースホルダーと想定しています。 メンバーの名前変更や削除は、互換性に影響する変更点です。 ユーザーからといって「占有」が含まれる名前も読み取りまたはドキュメントに従うをユーザーに依存できるメンバーを無視することはありません。 さらに、オブジェクト ブラウザーと優れた統合開発環境の予約済みのメンバーが表示される、ため、混乱が生じるどのメンバーが実際に使用されています。  
  
 予約済みのメンバーではなく、今後のバージョンで列挙型に新しいメンバーを追加します。 ほとんどの場合、新しいメンバーの追加が重大な変更として、追加の変更を元のメンバーの値は発生しません  
  
 元のメンバーは、元の値を保持する場合でも、限られた数のケースは、メンバーの追加、互換性に影響する変更です。 主に、新しいメンバーできません返される既存のコード パスから使用する呼び出し元を分断することがなく、 `switch` (`Select`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])、戻り値を全体のメンバーの一覧を含みますで例外をスローするステートメント、。既定のケース。 セカンダリ問題にならなければは、クライアント コードがリフレクション メソッドからの動作の変更など<xref:System.Enum.IsDefined%2A?displayProperty=fullName>です。 同様に、新しいメンバーが既存のメソッドから返される、または場合リフレクションの不適切な使用のための既知のアプリケーションの非互換性が発生した、のみ互換性に影響しない解決するには。  
  
1.  元と新しいメンバーを含む新しい列挙体を追加します。  
  
2.  元の列挙をマーク、<xref:System.ObsoleteAttribute?displayProperty=fullName>属性。  
  
 任意の外部から参照できる型または元の列挙体を公開するメンバーに対して同じ手順に従います。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するのには、削除するか、メンバーの名前を変更します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 現在使用されているメンバーのまたはが以前に出荷されたライブラリのこの規則による警告を抑制しても安全です。  
  
## <a name="related-rules"></a>関連規則  
 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1712: enum 値を型名のプレフィックスにしません](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: 列挙ストレージは Int32 でなければなりません](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1008: Enums は 0 値を含んでいなければなりません](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)