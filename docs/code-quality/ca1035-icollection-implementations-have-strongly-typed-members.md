---
title: 'CA1035: ICollection の実装が厳密に型指定されたメンバー |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82703b6572b1c491fba118360fc07ddda1b0c61f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: ICollection の実装は、厳密に型指定されたメンバーを含んでいます
|||  
|-|-|  
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|  
|CheckId|CA1035|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリックまたはプロテクト型が実装する<xref:System.Collections.ICollection?displayProperty=fullName>を厳密に型指定されたメソッドを提供しない場合が<xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>です。 厳密に型指定されたバージョンの<xref:System.Collections.ICollection.CopyTo%2A>2 つのパラメーターを受け入れる必要がありすることはできません、<xref:System.Array?displayProperty=fullName>または配列の<xref:System.Object?displayProperty=fullName>最初のパラメーターとして。  
  
## <a name="rule-description"></a>規則の説明  
 この規則で<xref:System.Collections.ICollection>強く指定を実装する型指定されたメンバー ユーザーは引数をキャストする必要がないように、<xref:System.Object>インターフェイスによって提供される機能を使用するときに入力します。 このルールは、ある型を実装する前提としています。<xref:System.Collections.ICollection>がよりも厳密な型のインスタンスのコレクションを管理するため<xref:System.Object>です。  
  
 <xref:System.Collections.ICollection> は、<xref:System.Collections.IEnumerable?displayProperty=fullName> インターフェイスを実装します。 場合は、コレクション内のオブジェクトを拡張<xref:System.ValueType?displayProperty=fullName>の厳密に型指定されたメンバーを指定する必要があります<xref:System.Collections.IEnumerable.GetEnumerator%2A>をボックス化によって発生したパフォーマンスの低下を回避します。 これは、コレクションのオブジェクトが参照型の場合に必要ありません。  
  
 インターフェイス メンバーの厳密に型指定されたバージョンを実装するインターフェイスのメンバーを明示的に実装形式で名前を使用して、`InterfaceName.InterfaceMemberName`など<xref:System.Collections.ICollection.CopyTo%2A>です。 明示的なインターフェイス メンバーは、インターフェイスで宣言されているデータ型を使用します。 インターフェイス メンバーの名前を使用して、厳密に型指定されたメンバーを実装する<xref:System.Collections.ICollection.CopyTo%2A>です。 Public として厳密に型指定されたメンバーを宣言し、パラメーターを宣言し、コレクションで管理されている厳密な型の値を返します。 厳密な型がなど弱い種類を置き換える<xref:System.Object>と<xref:System.Array>インターフェイスで宣言されています。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、インターフェイス メンバーを明示的に実装 (として宣言<xref:System.Collections.ICollection.CopyTo%2A>)。 として宣言されている、パブリックの厳密に型指定されたメンバーを追加`CopyTo`、最初のパラメーターとして厳密に型指定された配列を受け取ることがあるとします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 新しいオブジェクトに基づくなどのコレクション、バイナリ ツリーは、新しいコレクションを拡張する型が決まります、厳密な型を実装する場合は、この規則による警告を抑制します。 これらの型は、このルールに準拠し、厳密に型指定されたメンバーを公開する必要があります。  
  
## <a name="example"></a>例  
 次の例では、実装するための正しい方法<xref:System.Collections.ICollection>です。  
  
 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1038: 列挙子は厳密に型指定されていなければなりません](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039: リストは厳密に型指定されています](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>