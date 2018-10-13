---
title: 'Ca 2112: セキュリティで保護された型はフィールドを公開しない |Microsoft Docs'
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
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3c42de78a75a689b2f248edd66df8109bcd00583
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189664"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: セキュリティで保護された型はフィールドを公開してはなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型はパブリック フィールドを格納し、によってセキュリティ保護されて、[リンク確認要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)します。

## <a name="rule-description"></a>規則の説明
 リンク確認要求で保護されている型のインスタンスに対するアクセス権がコードにある場合、その型のフィールドにアクセスするためにリンク確認要求に適合する必要はありません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するのには、非パブリック フィールドを作成し、パブリック プロパティまたはフィールド データを返すメソッドを追加します。 Linkdemand 型では、型のプロパティおよびメソッドへのアクセスを保護します。 ただし、コード アクセス セキュリティは、フィールドには適用されません。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 両方のセキュリティの問題と適切なデザイン、パブリック フィールドの非パブリックのことで違反を修正する必要があります。 このルールから警告を抑制するには、フィールドはセキュリティで保護された、必要のある情報を保持しない場合と、フィールドの内容に依存しない場合。

## <a name="example"></a>例
 次の例は、ライブラリの種類で構成されます (`SecuredTypeWithFields`) 型、セキュリティ保護されていないフィールドを持つ (`Distributor`) インスタンス型には、それらを作成するアクセス許可はなく、アプリケーションのコードをライブラリの種類のインスタンスを作成することができます種類をセキュリティで保護するアクセス許可があるない場合でも、インスタンスのフィールドを読み取ることができます。

 次のライブラリ コードでは、この規則に違反します。

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>例
 アプリケーションでは、リンク確認要求、セキュリティで保護された型を保護するため、インスタンスを作成できません。 次のクラスは、セキュリティで保護された型のインスタンスを取得するアプリケーションを使用できます。

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>例
 次のアプリケーションは、方法、セキュリティで保護された型のメソッドへのアクセスの許可なくコード フィールドにアクセスできるかを示しています。

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **SecuredTypeWithFields のインスタンスを作成します。** 
**セキュリティで保護された型のフィールド: 22、33**
**セキュリティで保護された型のフィールドを変更しています.** 
**キャッシュ オブジェクトのフィールド: 99、33**
## <a name="related-rules"></a>関連規則
 [CA1051: 参照できるインスタンス フィールドを宣言しないでください](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>関連項目
 [リンク確認要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[データとモデリング](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



