---
title: "CA1039: リストは厳密に型指定されています | Microsoft Docs"
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
  - "CA1039"
  - "ListsAreStronglyTyped"
helpviewer_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1039: リストは厳密に型指定されています
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ListsAreStronglyTyped|  
|CheckId|CA1039|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型またはプロテクト型で <xref:System.Collections.IList?displayProperty=fullName> が実装されていますが、次の 1 つ以上の対象に厳密に型指定されたメソッドがありません。  
  
-   IList.Item  
  
-   IList.Add  
  
-   IList.Contains  
  
-   IList.IndexOf  
  
-   IList.Insert  
  
-   IList.Remove  
  
## 規則の説明  
 この規則では、<xref:System.Collections.IList> で厳密に型指定されたメンバーを実装する必要があります。これは、ユーザーがインターフェイスに備わっている機能を使用するときに、必ずしも引数を <xref:System.Object?displayProperty=fullName> 型にキャストするとは限らないためです。  <xref:System.Collections.IList> インターフェイスは、インデックスからアクセスできるオブジェクトのコレクションで実装されます。  この規則では、<xref:System.Collections.IList> を実装する型でこの処理を行って、<xref:System.Object> よりも厳密な型のインスタンス コレクションを管理すると想定しています。  
  
 <xref:System.Collections.IList> は、<xref:System.Collections.ICollection?displayProperty=fullName> インターフェイスと <xref:System.Collections.IEnumerable?displayProperty=fullName> インターフェイスを実装します。  <xref:System.Collections.IList> を実装する場合、<xref:System.Collections.ICollection> に必要な厳密に型指定されたメンバーを提示します。  コレクション内のオブジェクトで <xref:System.ValueType?displayProperty=fullName> を拡張する場合、<xref:System.Collections.IEnumerable.GetEnumerator%2A> に厳密に型指定したメンバーを提示します。これによって、ボックス化によるパフォーマンスの低下を防ぐことができます。コレクションのオブジェクトが参照型である場合、この処理は必要ありません。  
  
 この規則を順守するには、InterfaceName.InterfaceMemberName の形式の名前 \(たとえば <xref:System.Collections.IList.Add%2A>\) で、インターフェイスのメンバーを明示的に実装します。  明示的なインターフェイス メンバーでは、インターフェイスで宣言されたデータ型を使用します。  `Add` などのインターフェイス メンバー名を使用して、厳密に型指定されたメンバーを実装します。  厳密に型指定されたメンバーをパブリックと宣言し、パラメーターと戻り値は、コレクションで管理される厳密な型になるように宣言します。  インターフェイスで宣言されている <xref:System.Object> や <xref:System.Array> などの弱い型は、厳密な型で置換されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.Collections.IList> メンバーを明示的に実装し、上記のメンバーを厳密に型指定したメンバーで置き換えます。  <xref:System.Collections.IList> インターフェイスを適切に実装し、必要な厳密に型指定されたメンバーを提示したコードについては、以下の例を参照してください。  
  
## 警告を抑制する状況  
 リンクされるリストは、新しいコレクションを拡張する型によって厳密な型が決まります。このように新しいオブジェクト ベースのコレクションを実装する場合は、この規則による警告を抑制します。  このような型では、この規則を順守し、厳密に型指定されたメンバーを公開します。  
  
## 使用例  
 次の例では、型 `YourType` によって <xref:System.Collections.CollectionBase?displayProperty=fullName> を拡張し、すべてのコレクションが厳密に型指定されます。  <xref:System.Collections.CollectionBase> は、<xref:System.Collections.IList> インターフェイスを明示的に実装しています。  そのため、<xref:System.Collections.IList> と <xref:System.Collections.ICollection> に対して、厳密に型指定されたメンバーのみを提示する必要があります。  
  
 [!code-cs[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]  
  
## 関連規則  
 [CA1035: ICollection の実装は、厳密に型指定されたメンバーを含んでいます](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1038: 列挙子は厳密に型指定されていなければなりません](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
## 参照  
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.IList?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>