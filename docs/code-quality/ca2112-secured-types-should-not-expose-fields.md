---
title: 'Ca 2112: セキュリティで保護された型はフィールドを公開しません |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 050aa2a5048ed4d58e6b5a285f584eda330f178f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: セキュリティで保護された型はフィールドを公開してはなりません
|||  
|-|-|  
|TypeName|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリックまたはプロテクト型はパブリック フィールドが含まれで保護されて、[リンク確認要求](/dotnet/framework/misc/link-demands)です。  
  
## <a name="rule-description"></a>規則の説明  
 リンク確認要求で保護されている型のインスタンスに対するアクセス権がコードにある場合、その型のフィールドにアクセスするためにリンク確認要求に適合する必要はありません。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、パブリックでないフィールドを作成し、パブリック プロパティまたはフィールド データを返すメソッドを追加します。 型に対する LinkDemand セキュリティ チェックは、型のプロパティおよびメソッドへのアクセスを保護します。 ただし、コード アクセス セキュリティは、フィールドには適用されません。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 両方のセキュリティの問題と適切なデザイン、パブリック フィールド非公開にすることで違反の修正する必要があります。 フィールドは、セキュリティで保護されたままにする必要があります情報を保持していない場合は、この規則による警告を抑制することができ、フィールドの内容に依存しないでください。  
  
## <a name="example"></a>例  
 次の例は、ライブラリの種類で構成されます (`SecuredTypeWithFields`) セキュリティ保護されていないフィールドを型を持つ (`Distributor`) 型にインスタンスには、それらを作成する権限はありませんおよびアプリケーションのコードをライブラリ型のインスタンスを作成することができます。種類を保護するアクセス許可があるない場合でも、インスタンスのフィールドを読み取ることができます。  
  
 次のライブラリ コードでは、この規則に違反します。  
  
 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## <a name="example"></a>例  
 アプリケーションでは、リンク確認要求をセキュリティで保護の種類を保護するため、インスタンスを作成できません。 次のクラスを使用すると、アプリケーションのセキュリティで保護された型のインスタンスを取得します。  
  
 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
## <a name="example"></a>例  
 次のアプリケーションは、方法、セキュリティで保護された型のメソッドにアクセスする権限がないコードがアクセスできるフィールドを示しています。  
  
 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
 **SecuredTypeWithFields のインスタンスを作成します。**  
**型のフィールドをセキュリティで保護: 22、33**  
**セキュリティで保護された型のフィールドを変更しています.**  
**オブジェクトのフィールドをキャッシュ: 99、33**   
## <a name="related-rules"></a>関連規則  
 [CA1051: 参照できるインスタンス フィールドを宣言しないでください](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>関連項目  
 [リンク確認要求](/dotnet/framework/misc/link-demands)   
 [データとモデリング](/dotnet/framework/data/index)