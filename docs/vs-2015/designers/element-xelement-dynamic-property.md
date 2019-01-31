---
title: Element (XElement 動的プロパティ) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e7789a94c38f7c6d7db22d9214b19857e4c62055
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753888"
---
# <a name="element-xelement-dynamic-property"></a>Element (XElement 動的プロパティ)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定された拡張名に対応する子要素のインスタンスを取得するためのインデクサーを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 `XElement Item(String expandedName)` 型のインデクサー。 このインデクサーは、拡張名のパラメーターを取得し、対応する <xref:System.Xml.Linq.XElement> を返します。指定された名前を持つ要素がない場合は、`null` を返します。  
  
## <a name="remarks"></a>コメント  
 このプロパティは、<xref:System.Xml.Linq.XContainer.Element%2A> クラスの <xref:System.Xml.Linq.XContainer?displayProperty=fullName> メソッドに相当します。  
  
## <a name="see-also"></a>「  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [XElement クラスの動的プロパティ](../designers/xelement-class-dynamic-properties.md)   
 [要素](../designers/elements-xelement-dynamic-property.md)
