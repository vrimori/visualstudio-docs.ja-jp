---
title: '1058: 型は一定の基本型を拡張するありません |Microsoft Docs'
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
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a4ffbe3b359f2c58f8e301b9176981a2037c17f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912436"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: 型は、一定の基本型を拡張することはできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照可能な型では、特定の基本型が拡張されます。 現在、このルールは、次の種類から派生した型を報告します。

-   <xref:System.ApplicationException?displayProperty=fullName>

-   <xref:System.Xml.XmlDocument?displayProperty=fullName>

-   <xref:System.Collections.CollectionBase?displayProperty=fullName>

-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>

-   <xref:System.Collections.Queue?displayProperty=fullName>

-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

-   <xref:System.Collections.SortedList?displayProperty=fullName>

-   <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>規則の説明
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 1 のバージョンから新しい例外を派生させるが推奨されました<xref:System.ApplicationException>します。 推奨設定が変更され、新しい例外の派生元<xref:System.Exception?displayProperty=fullName>またはそのサブクラス内の 1 つ、<xref:System>名前空間。

 サブクラスを作成しない<xref:System.Xml.XmlDocument>かどうかは、基になるオブジェクト モデルまたはデータ ソースの XML ビューを作成します。

### <a name="non-generic-collections"></a>非ジェネリック コレクション
 使用して、または可能であれば、ジェネリック コレクションを拡張します。 以前に発送した場合を除き、コードで、非ジェネリック コレクションは拡張されません。

 **不適切な使用方法の例**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **正しい使用法の例**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するのには、別の基本型またはジェネリック コレクションから型を派生します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 詳細についてはこの規則違反の警告を抑制しないでください<xref:System.ApplicationException>します。 この規則違反の警告を抑制するには、安全では<xref:System.Xml.XmlDocument>します。 コードが以前にリリースされた場合は、非ジェネリック コレクションについて警告を抑制しても安全です。



