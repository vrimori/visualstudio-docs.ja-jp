---
title: '2111: ca ポインターできません表示 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 512d253a4e6cf4d8c92f7091d96cc747a667a646
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589673"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: ポインターは参照可能にすることはできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA2111: ポインターを表示することはできません](https://docs.microsoft.com/visualstudio/code-quality/ca2111-pointers-should-not-be-visible)します。

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト<xref:System.IntPtr?displayProperty=fullName>または<xref:System.UIntPtr?displayProperty=fullName>フィールドは読み取り専用ではありません。

## <a name="rule-description"></a>規則の説明
 <xref:System.IntPtr> <xref:System.UIntPtr>はアンマネージ メモリへのアクセスに使用されるポインター型。 ポインターは、private、internal、または読み取り専用には、悪意のあるコードは、メモリ内の任意の場所へのアクセスを許可またはアプリケーションまたはシステム エラーが発生する可能性があるポインターの値を変更できます。

 ポインターのフィールドを含む型に安全にアクセスする場合を参照してください。 [ca 2112: セキュリティで保護された型はフィールドを公開する必要があります](../code-quality/ca2112-secured-types-should-not-expose-fields.md)します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 読み取り専用、internal、またはプライベートにすることで、ポインターを保護します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 ポインターの値に依存しない場合は、この規則による警告を抑制します。

## <a name="example"></a>例
 次のコードでは、ルールを満たすために違反するポインターを示します。 プライベートでないポインターも規則に違反することに注意してください[ca 1051: 参照できるインスタンス フィールドを宣言しない](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)します。

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA2112: セキュリティで保護された型はフィールドを公開してはなりません](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: 参照できるインスタンス フィールドを宣言しないでください](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>関連項目
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>



