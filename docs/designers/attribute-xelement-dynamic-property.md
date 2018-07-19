---
title: Attribute (XElement 動的プロパティ)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: caacdd787f1765721d281db885364aafc36c5183
ms.sourcegitcommit: 522ba712c0d625e51352506146b0556414681964
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2018
ms.locfileid: "37890010"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (XElement 動的プロパティ)

指定された拡張名に対応する属性のインスタンスの取得に使用するインデクサーを取得します。

## <a name="syntax"></a>構文

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>プロパティ値/戻り値

`XAttribute Item(String expandedName)` 型のインデクサー。 このインデクサーは、指定された属性の展開名を受け取り、対応する <xref:System.Xml.Linq.XAttribute> を返します。指定された名前を持つ属性がない場合は、`null` を返します。

## <a name="remarks"></a>コメント

このプロパティは、<xref:System.Xml.Linq.XElement.Attribute%2A> クラスの <xref:System.Xml.Linq.XElement?displayProperty=fullName> メソッドに相当します。

## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [XElement クラスの動的プロパティ](../designers/xelement-class-dynamic-properties.md)
- [値](../designers/value-xattribute-dynamic-property.md)