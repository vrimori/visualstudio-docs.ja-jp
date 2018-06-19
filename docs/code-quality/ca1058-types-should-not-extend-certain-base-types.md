---
title: 'CA1058: 型は、一定の基本型を拡張することはできません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3c1e4635a654cac608985766884ddb66e353d03
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898277"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: 型は、一定の基本型を拡張することはできません
|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照可能な型では、特定の基本型が拡張されます。 現時点では、このルールは、次の種類から派生した型を報告します。

-   <xref:System.ApplicationException?displayProperty=fullName>

-   <xref:System.Xml.XmlDocument?displayProperty=fullName>

-   <xref:System.Collections.CollectionBase?displayProperty=fullName>

-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>

-   <xref:System.Collections.Queue?displayProperty=fullName>

-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

-   <xref:System.Collections.SortedList?displayProperty=fullName>

-   <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>規則の説明
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 1 のバージョンから新しい例外を派生させるが推奨されました<xref:System.ApplicationException>です。 推奨設定が変更され、新しい例外の派生元<xref:System.Exception?displayProperty=fullName>またはそのサブクラス内の 1 つ、<xref:System>名前空間。

 サブクラスを作成しない<xref:System.Xml.XmlDocument>を基になるオブジェクト モデルまたはデータ ソースの XML ビューを作成するかどうか。

### <a name="non-generic-collections"></a>非ジェネリック コレクション
 使用させたり、拡張可能な場合、ジェネリック コレクション。 以前に出荷する場合を除き、コード内の非ジェネリック コレクションを拡張しません。

 **不適切な使用例**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **正しい使用例**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、別の基本型またはジェネリック コレクションから型を派生します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 違反に対するこの規則による警告は抑制しないでください<xref:System.ApplicationException>です。 安全にに関する違反に対するこの規則による警告は抑制<xref:System.Xml.XmlDocument>です。 コードが以前にリリースされた場合は、非ジェネリック コレクションについて警告を抑制しても安全です。