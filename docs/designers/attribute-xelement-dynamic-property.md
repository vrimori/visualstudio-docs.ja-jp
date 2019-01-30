---
title: Attribute (XElement 動的プロパティ)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b81800e97b02657bd296076803171dda23f65d6f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001762"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (XElement 動的プロパティ)

指定された拡張名に対応する属性のインスタンスの取得に使用するインデクサーを取得します。

## <a name="syntax"></a>構文

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>プロパティ値/戻り値

`XAttribute Item(String expandedName)` 型のインデクサー。 このインデクサーは、指定された属性の拡張名を受け取り、対応する <xref:System.Xml.Linq.XAttribute> を返します。指定された名前を持つ属性がない場合は、`null` を返します。

## <a name="remarks"></a>コメント

このプロパティは、<xref:System.Xml.Linq.XElement.Attribute%2A> クラスの <xref:System.Xml.Linq.XElement?displayProperty=fullName> メソッドに相当します。

## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [XElement クラスの動的プロパティ](../designers/xelement-class-dynamic-properties.md)
- [[値]](../designers/value-xattribute-dynamic-property.md)