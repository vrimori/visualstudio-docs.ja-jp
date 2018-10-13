---
title: 'Ca 2105: 配列フィールドを読み取ることができませんのみ |Microsoft Docs'
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
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a310957f1552e289993643d39965d8a6a8693fe2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207949"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: 配列フィールドは読み取り専用にできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 読み取り専用配列を保持するパブリックまたはプロテクト フィールドが宣言されています。

## <a name="rule-description"></a>規則の説明
 適用すると、 `readonly` (`ReadOnly`で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 修飾子を配列フィールドを含むフィールドを変更して、別の配列を参照してくださいことはできません。 ただし、読み取り専用フィールドに格納された配列の要素は変更できます。 判断したり、パブリックにアクセスできる読み取り専用配列の要素に基づく操作を実行するコードには、悪用可能なセキュリティの脆弱性が含まれます。

 メモをパブリック フィールドを持つデザイン規則に違反しても[ca 1051: 参照できるインスタンス フィールドを宣言しません](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールで識別されるセキュリティの脆弱性を修正するのに依存しないパブリックにアクセスできる読み取り専用配列の内容。 次の手順のいずれかを使用することを強くお勧めします。

-   厳密に型指定されたコレクションは変更できない配列に置き換えます。 詳細については、「 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName> 」を参照してください。

-   プライベート配列の複製を返すメソッドでは、パブリック フィールドを置き換えます。 コードが、複製に依存しないためにありません危険要素が変更された場合です。

 2 番目の方法を選択した場合、フィールドと置き換えないでプロパティ悪影響を与える、配列を返すプロパティは、パフォーマンスに影響します。 詳細については、次を参照してください。 [ca 1819: プロパティは、配列を返す必要がありますいない](../code-quality/ca1819-properties-should-not-return-arrays.md)します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告の除外はお勧めします。 読み取り専用フィールドの内容が重要ではない場合はほとんどありませんが発生します。 シナリオの場合は場合、削除、`readonly`修飾子の代わりに、メッセージを除外します。

## <a name="example"></a>例
 この例では、この規則に違反する危険性を示します。 最初の部分は、型を持つサンプル ライブラリを示しています。 `MyClassWithReadOnlyArrayField`、2 つのフィールドを格納している (`grades`と`privateGrades`) を安全ではありません。 フィールド`grades`はパブリックであり、そのため、呼び出し元に対して脆弱になります。 フィールド`privateGrades`はプライベートであるが、呼び出し元に返されるため、脆弱なままです、`GetPrivateGrades`メソッド。 `securePrivateGrades`フィールドが、安全な方法で公開されている、`GetSecurePrivateGrades`メソッド。 優れた設計のプラクティスに従うにはプライベートとして宣言されています。 2 番目の部分に格納された値を変更するコードを示しています、`grades`と`privateGrades`メンバー。

 サンプルのクラス ライブラリは、次の例が表示されます。

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>例
 次のコードでは、読み取り専用配列セキュリティの問題を説明するために、例のクラス ライブラリを使用します。

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 この例の出力は次のとおりです。

 **改ざんする前に: 成績: 90, 90、90 プライベート成績: 90, 90、90 をセキュリティで保護の成績、90、90、90**
**改ざん後: 成績: 90、555、90 プライベート成績: 90、555、90 をセキュリティで保護の成績、90、90、90**
## <a name="see-also"></a>関連項目
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>



