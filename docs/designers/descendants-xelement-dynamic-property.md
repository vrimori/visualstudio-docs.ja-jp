---
title: Descendants (XElement 動的プロパティ)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7255753445d014b1ab59f6e2e8143b341b28a892
ms.sourcegitcommit: 522ba712c0d625e51352506146b0556414681964
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2018
ms.locfileid: "37890254"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (XElement 動的プロパティ)

現在の要素の子孫要素のうち指定された拡張名に一致するすべての子孫要素を取得するためのインデクサーを取得します。

## <a name="syntax"></a>構文

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>プロパティ値/戻り値

`IEnumerable<XElement> Item(String expandedName)` 型のインデクサー。 このインデクサーは、指定された子孫要素の展開名を受け取り、<xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` コレクション内の一致する子要素を返します。

## <a name="remarks"></a>コメント

このプロパティは、<xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> クラスの <xref:System.Xml.Linq.XContainer> メソッドに相当します。

返されるコレクション内の要素は、XML ソース ドキュメント順になります。

このプロパティは、遅延実行を使用します。

## <a name="see-also"></a>関連項目

- [XElement クラスの動的プロパティ](../designers/xelement-class-dynamic-properties.md)
- [要素](../designers/elements-xelement-dynamic-property.md)