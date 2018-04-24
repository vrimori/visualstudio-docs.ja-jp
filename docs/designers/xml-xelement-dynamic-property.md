---
title: XML (XElement 動的プロパティ)
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 36b2100218267587e2ea5d38ad62f7ed28dbc102
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="xml-xelement-dynamic-property"></a>XML (XElement 動的プロパティ)

要素について、書式設定されていない XML コンテンツを取得します。

## <a name="syntax"></a>構文

```
elem.Xml
```

## <a name="property-valuereturn-value"></a>プロパティ値/戻り値

要素に関する書式設定されていない XML コンテンツを表す <xref:System.String>。

## <a name="remarks"></a>コメント

このプロパティは、<xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> パラメーターが <xref:System.Xml.Linq.XNode?displayProperty=fullName> に設定されている、`SaveOptions` クラスの <xref:System.Xml.Linq.SaveOptions> メソッドに相当します。

## <a name="see-also"></a>関連項目

- [XElement クラスの動的プロパティ](../designers/xelement-class-dynamic-properties.md)
- [値](../designers/value-xelement-dynamic-property.md)