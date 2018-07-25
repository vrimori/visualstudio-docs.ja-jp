---
title: Element (XElement 動的プロパティ)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf8d964a41193d1db845a608749b0ca671dd9349
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924054"
---
# <a name="element-xelement-dynamic-property"></a>Element (XElement 動的プロパティ)

指定された拡張名に対応する子要素のインスタンスを取得するためのインデクサーを取得します。

## <a name="syntax"></a>構文

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>プロパティ値/戻り値

`XElement Item(String expandedName)` 型のインデクサー。 このインデクサーは、展開名のパラメーターを取得し、対応する <xref:System.Xml.Linq.XElement> を返します。指定された名前を持つ要素がない場合は、`null` を返します。

## <a name="remarks"></a>コメント

このプロパティは、<xref:System.Xml.Linq.XContainer.Element%2A> クラスの <xref:System.Xml.Linq.XContainer?displayProperty=fullName> メソッドに相当します。

## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [XElement クラスの動的プロパティ](../designers/xelement-class-dynamic-properties.md)
- [要素](../designers/elements-xelement-dynamic-property.md)