---
title: "CA1035: ICollection の実装は、厳密に型指定されたメンバーを含んでいます | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICollectionImplementationsHaveStronglyTypedMembers"
  - "CA1035"
helpviewer_keywords: 
  - "CA1035"
  - "ICollectionImplementationsHaveStronglyTypedMembers"
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1035: ICollection の実装は、厳密に型指定されたメンバーを含んでいます
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|  
|CheckId|CA1035|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型またはプロテクト型で、<xref:System.Collections.ICollection?displayProperty=fullName> を実装していますが、厳密に型指定されたメソッドが <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> にありません。  厳密に型指定されたバージョンの <xref:System.Collections.ICollection.CopyTo%2A> では、2 つのパラメーターを受け入れる必要があります。また、最初のパラメーターに <xref:System.Array?displayProperty=fullName> または <xref:System.Object?displayProperty=fullName> の配列を指定することはできません。  
  
## 規則の説明  
 この規則では、<xref:System.Collections.ICollection> で厳密に型指定されたメンバーを実装する必要があります。これは、ユーザーがインターフェイスに備わっている機能を使用するときに、必ずしも引数を <xref:System.Object> 型にキャストするとは限らないためです。  この規則では、<xref:System.Collections.ICollection> を実装する型でこの処理を行って、<xref:System.Object> よりも厳密な型のインスタンス コレクションを管理すると想定しています。  
  
 <xref:System.Collections.ICollection> では、<xref:System.Collections.IEnumerable?displayProperty=fullName> インターフェイスを実装します。  コレクション内のオブジェクトで <xref:System.ValueType?displayProperty=fullName> を拡張する場合、<xref:System.Collections.IEnumerable.GetEnumerator%2A> に厳密に型指定したメンバーを提示します。これによって、ボックス化によるパフォーマンスの低下を防ぐことができます。  コレクションのオブジェクトが参照型である場合、この処理は必要ありません。  
  
 厳密に型指定されたバージョンのインターフェイス メンバーを実装するには、明示的に `InterfaceName.InterfaceMemberName` という形式の名前を使用して、インターフェイス メンバーを実装します \(たとえば <xref:System.Collections.ICollection.CopyTo%2A>\)。  明示的なインターフェイス メンバーでは、インターフェイスで宣言されたデータ型を使用します。  <xref:System.Collections.ICollection.CopyTo%2A> などのインターフェイス メンバー名を使用して、厳密に型指定されたメンバーを実装します。  厳密に型指定されたメンバーをパブリックと宣言し、パラメーターと戻り値は、コレクションで管理される厳密な型になるように宣言します。  インターフェイスで宣言されている <xref:System.Object> や <xref:System.Array> などの弱い型は、厳密な型で置換されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、インターフェイス メンバーを明示的に実装します \(<xref:System.Collections.ICollection.CopyTo%2A> と宣言します\)。  厳密に型指定されたパブリック メンバーを追加し、`CopyTo` と宣言して、厳密に型指定された配列を最初のパラメーターに使用します。  
  
## 警告を抑制する状況  
 バイナリ ツリーは、新しいコレクションを拡張する型によって厳密な型が決まります。このように新しいオブジェクト ベースのコレクションを実装するときは、この規則による警告を抑制します。  このような型では、この規則を順守し、厳密に型指定されたメンバーを公開します。  
  
## 使用例  
 <xref:System.Collections.ICollection> の適切な実装例を次に示します。  
  
 [!code-cs[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## 関連規則  
 [CA1038: 列挙子は厳密に型指定されていなければなりません](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039: リストは厳密に型指定されています](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## 参照  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>