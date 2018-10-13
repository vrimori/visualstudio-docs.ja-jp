---
title: '1700 ca: いない名前列挙型値&#39;占有&#39;|Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 58b1d329447ab73f9df93d2f75a62c2e21a6dcfc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204725"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>1700 ca: いない名前列挙型値&#39;予約済み&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 列挙体のメンバーの名前には、「予約」という単語が含まれています。

## <a name="rule-description"></a>規則の説明
 この規則では、"reserved" を含む名前の列挙体のメンバーは、現在使用されていなくても、将来的なバージョンでは名前を変更するか削除されるプレースホルダーと想定しています。 メンバーの名前変更や削除は、互換性に影響する変更点です。 ユーザーが「予約」が含まれる名前も、ユーザーに読み取りまたはドキュメントに従うに依存することができますので、単にメンバーを無視することはありません。 さらに、予約済みのメンバーは、統合開発環境、オブジェクト ブラウザーで表示される、ためするメンバーが実際に使用されているについて混乱が発生することができます。

 予約済みのメンバーを使用する代わりには、今後のバージョンで列挙型に新しいメンバーを追加します。 ほとんどの場合、新しいメンバーの追加は重大な変更として、追加の変更を元のメンバーの値は発生しません。

 元のメンバーは、元の値を保持する場合でも、ケースの数に制限は、メンバーの追加、互換性に影響する変更です。 主に、新しいメンバーは返せません既存のコード パスからを使用する呼び出し元を損なうことがなく、 `switch` (`Select`で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)])、戻り値全体のメンバーの一覧を包含して、例外をスローするステートメント、既定のケース。 セカンダリの問題は、クライアント コードがリフレクション メソッドからの動作の変更など<xref:System.Enum.IsDefined%2A?displayProperty=fullName>します。 したがって、新しいメンバーが既存のメソッドから返される、またはリフレクションの不適切な使用状況が発生する既知のアプリケーションの互換性がない、互換性に影響しないが唯一のソリューションに。

1.  元と新しいメンバーを含む新しい列挙体を追加します。

2.  元の列挙を<xref:System.ObsoleteAttribute?displayProperty=fullName>属性。

 外部から参照できる型またはメンバーを元の列挙型を公開するのと同じ手順に従います。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、削除またはメンバーの名前を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 現在使用されているメンバーのまたはが以前に出荷されたライブラリのこの規則による警告を抑制しても安全です。

## <a name="related-rules"></a>関連規則
 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712: enum 値を型名のプレフィックスにしません](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: 列挙ストレージは Int32 でなければなりません](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008: Enums は 0 値を含んでいなければなりません](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)



