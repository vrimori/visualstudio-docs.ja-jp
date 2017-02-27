---
title: "CA1038: 列挙子は厳密に型指定されていなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EnumeratorsShouldBeStronglyTyped"
  - "CA1038"
helpviewer_keywords: 
  - "CA1038"
  - "EnumeratorsShouldBeStronglyTyped"
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1038: 列挙子は厳密に型指定されていなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumeratorsShouldBeStronglyTyped|  
|CheckId|CA1038|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型またはプロテクト型で、<xref:System.Collections.IEnumerator?displayProperty=fullName> を実装していますが、厳密に型指定されたバージョンの <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> プロパティがありません。  次の型から派生した型は、この規則ではチェックされません。  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## 規則の説明  
 この規則では、<xref:System.Collections.IEnumerator> で、厳密に型指定されたバージョンの <xref:System.Collections.IEnumerator.Current%2A> プロパティを実装する必要があります。これは、ユーザーは、インターフェイスに備わっている機能を使用するときに、厳密な型に必ずしも戻り値をキャストするとは限らないためです。  この規則では、<xref:System.Collections.IEnumerator> を実装する型に、<xref:System.Object> よりも厳密な型のインスタンス コレクションが含まれていると想定しています。  
  
## 違反の修正方法  
 この規則違反を修正するには、インターフェイス プロパティを明示的に実装します \(`IEnumerator.Current` と宣言します\)。  厳密に型指定されたパブリック プロパティを追加し、`Current` と宣言し、厳密に型指定されたオブジェクトを戻すようにします。  
  
## 警告を抑制する状況  
 オブジェクト ベースのコレクション \(バイナリ ツリーなど\) と使用する目的でオブジェクト ベースの列挙子を実装する場合は、この規則による警告を抑制します。  新しいコレクションを拡張する型では、厳密に型指定した列挙子を定義し、厳密に型指定したプロパティを公開します。  
  
## 使用例  
 厳密に型指定された <xref:System.Collections.IEnumerator> の適切な実装例を次に示します。  
  
 [!CODE [FxCop.Design.IEnumeratorStrongTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes#1)]  
  
## 関連規則  
 [CA1035: ICollection の実装は、厳密に型指定されたメンバーを含んでいます](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039: リストは厳密に型指定されています](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## 参照  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>