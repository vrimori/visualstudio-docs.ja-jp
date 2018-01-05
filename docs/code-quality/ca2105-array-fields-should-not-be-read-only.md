---
title: "Ca 2105: 配列フィールドを読み込まないでのみ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c791bfaa652570767a5ea0f3fa351b1b3b88b068
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: 配列フィールドは読み取り専用にできません
|||  
|-|-|  
|TypeName|ArrayFieldsShouldNotBeReadOnly|  
|CheckId|CA2105|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 配列を保持するパブリックまたはプロテクト フィールドは読み取り専用に宣言されます。  
  
## <a name="rule-description"></a>規則の説明  
 適用すると、 `readonly` (`ReadOnly`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])、別の配列を参照してくださいに配列のフィールドを含むフィールドに修飾子を変更できません。 ただし、読み取り専用フィールドに格納された配列の要素は変更できます。 決定を下すまたはパブリックにアクセスできる読み取り専用配列の要素に基づく操作を実行するコードには、利用可能なセキュリティの脆弱性が含まれます。  
  
 注いるパブリック フィールドを持つデザイン規則に違反するも[ca 1051: 参照できるインスタンス フィールドを宣言しません](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)です。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 このルールによって識別されるセキュリティの脆弱性を修正するに依存しないパブリックにアクセスできる読み取り専用配列の内容。 次の手順のいずれかを使用することを強くお勧めします。  
  
-   厳密に型指定されたコレクションは変更できない配列を置き換えます。 詳細については、「<xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>」を参照してください。  
  
-   プライベート配列のクローンを返すメソッドでパブリック フィールドを置き換えます。 コードが、複製に依存しないためにはありません危険要素が変更された場合です。  
  
 2 番目の方法を選択した場合を置き換えないフィールド プロパティを設定します。配列を返す悪影響を及ぼすプロパティでは、パフォーマンスに影響します。 詳細については、次を参照してください。 [ca 1819: プロパティは、配列を返す必要がありますいない](../code-quality/ca1819-properties-should-not-return-arrays.md)です。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告の除外はお勧めします。 読み取り専用フィールドの内容が重要ではない場合はほとんどありませんが発生します。 場合は、シナリオの場合は、削除、`readonly`修飾子の代わりに、メッセージを除外します。  
  
## <a name="example"></a>例  
 この例では、この規則違反の危険性を示します。 最初の部分は、型を持つサンプル ライブラリを示しています。 `MyClassWithReadOnlyArrayField`、2 つのフィールドを格納している (`grades`と`privateGrades`) を安全ではありません。 フィールド`grades`がパブリックであり、したがって、呼び出し元に脆弱性が存在します。 フィールド`privateGrades`プライベートは引き続き脆弱で呼び出し元に返されるため、`GetPrivateGrades`メソッドです。 `securePrivateGrades`フィールドが、安全な方法で公開されている、`GetSecurePrivateGrades`メソッドです。 優れた設計のプラクティスに従ってくださいにプライベートとして宣言されています。 2 番目の部分に格納された値を変更するコードを示しています、`grades`と`privateGrades`メンバー。  
  
 サンプルのクラス ライブラリは、次の例が表示されます。  
  
 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]  
  
## <a name="example"></a>例  
 次のコードは、読み取り専用配列セキュリティの問題を説明するためにサンプルのクラス ライブラリを使用します。  
  
 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]  
  
 この例から出力されます。  
  
 **改ざんする前に: グレード: 90、90、90 プライベート グレード: 90、90、90 Secure 成績、90、90、90**  
**改ざん後: グレード: 90、555、90 プライベート グレード: 90、555、90 Secure 成績、90、90、90**   
## <a name="see-also"></a>参照  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>