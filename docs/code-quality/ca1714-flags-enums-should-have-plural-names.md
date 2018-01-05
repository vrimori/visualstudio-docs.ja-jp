---
title: "1714: ca フラグ列挙いなければなりません複数形の名前 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 82f5e18b838e6f6c0696359a9d88ba3350e636ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: フラグ列挙は、複数形の名前を含んでいなければなりません
|||  
|-|-|  
|TypeName|FlagsEnumsShouldHavePluralNames|  
|CheckId|CA1714|  
|カテゴリ|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリック列挙体には、<xref:System.FlagsAttribute?displayProperty=fullName>し、その名前が終わらないでの ' です。  
  
## <a name="rule-description"></a>規則の説明  
 マークされた型<xref:System.FlagsAttribute>は属性が 1 つ以上の値を指定できることを示すために複数形の名前します。 たとえば、週の曜日を定義する列挙値可能性がありますを想定しているアプリケーションで使用する複数の曜日を指定できます。 この列挙体である必要があります、<xref:System.FlagsAttribute>呼べるものは「日」とします。 指定する 1 日だけを許可するような列挙体は、属性はありませんし、可能性があります 'Day' と呼ばれます。  
  
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージ コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 複数形の語の列挙体の名前を作成または削除、<xref:System.FlagsAttribute>属性の場合は、複数の列挙値は同時に指定しないでください。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 名前には、複数形の語で終わらない場合は、違反を抑制するのには安全ではの ' です。 たとえば、以前説明した複数の曜日列挙することは DaysOfTheWeek' という名前が、これと、ルールがありませんのロジックが違反していました。 このような違反は、抑制をする必要があります。  
  
## <a name="related-rules"></a>関連規則  
 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>参照  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [列挙型デザイン](/dotnet/standard/design-guidelines/enum)