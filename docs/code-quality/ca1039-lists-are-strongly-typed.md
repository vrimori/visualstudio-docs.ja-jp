---
title: 'CA1039: リストは厳密に型指定されています'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70bc0065957321894c53726790b73b432dfdea6f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31901041"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: リストは厳密に型指定されています
|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型を実装して<xref:System.Collections.IList?displayProperty=fullName>は、次の 1 つ以上の厳密に型指定されたメソッドは提供しません。

-   IList.Item

-   IList.Add

-   IList.Contains

-   IList.IndexOf

-   IList.Insert

-   IList.Remove

## <a name="rule-description"></a>規則の説明
 この規則で<xref:System.Collections.IList>強く指定を実装する型指定されたメンバー ユーザーは引数をキャストする必要がないように、<xref:System.Object?displayProperty=fullName>インターフェイスによって提供される機能を使用するときに入力します。 <xref:System.Collections.IList>インターフェイス インデックスによってアクセスできるオブジェクトのコレクションによって実装されます。 このルールは、ある型を実装する前提としています。<xref:System.Collections.IList>はこれよりも厳密な型のインスタンスのコレクションを管理する<xref:System.Object>です。

 <xref:System.Collections.IList> 実装する、<xref:System.Collections.ICollection?displayProperty=fullName>と<xref:System.Collections.IEnumerable?displayProperty=fullName>インターフェイスです。 実装する場合<xref:System.Collections.IList>の必須の厳密に型指定されたメンバーを指定する必要があります<xref:System.Collections.ICollection>です。 場合は、コレクション内のオブジェクトを拡張<xref:System.ValueType?displayProperty=fullName>の厳密に型指定されたメンバーを指定する必要があります<xref:System.Collections.IEnumerable.GetEnumerator%2A>パフォーマンスの低下を避けるためにボックス化によって発生した以外の場合は、コレクションのオブジェクトが参照型の場合必要はありません。

 この規則に準拠、インターフェイスのメンバーを明示的に実装など InterfaceName.InterfaceMemberName、フォームの名前を使用して<xref:System.Collections.IList.Add%2A>です。 明示的なインターフェイス メンバーは、インターフェイスで宣言されているデータ型を使用します。 インターフェイス メンバーの名前を使用して、厳密に型指定されたメンバーを実装する`Add`です。 Public として厳密に型指定されたメンバーを宣言し、パラメーターを宣言し、コレクションで管理されている厳密な型の値を返します。 厳密な型がなど弱い種類を置き換える<xref:System.Object>と<xref:System.Array>インターフェイスで宣言されています。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、明示的に実装<xref:System.Collections.IList>メンバーし、前述のメンバーの厳密に型指定の代替手段を提供します。 正しく実装するコードを<xref:System.Collections.IList>インターフェイスし、必要なは、厳密に型指定されたメンバーは、次の例を参照してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 新しいオブジェクトに基づくなど、コレクション、新しいコレクションを拡張する型が厳密な型を判断、リンク リストを実装する場合は、この規則による警告を抑制します。 これらの型は、このルールに準拠し、厳密に型指定されたメンバーを公開する必要があります。

## <a name="example"></a>例
 次の例では、型`YourType`拡張<xref:System.Collections.CollectionBase?displayProperty=fullName>すべて厳密に型指定されたコレクションと同様、します。 なお<xref:System.Collections.CollectionBase>の明示的な実装を提供、<xref:System.Collections.IList>のためのインターフェイスです。 したがって、のみを指定してください、厳密に型指定されたメンバーの<xref:System.Collections.IList>と<xref:System.Collections.ICollection>です。

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA1035: ICollection の実装は、厳密に型指定されたメンバーを含んでいます](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: 列挙子は厳密に型指定されていなければなりません](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>関連項目
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName> <xref:System.Collections.IList?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>