---
title: Elements (XElement 動的プロパティ) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b65f32cc4146f275ec77a5942bdfef3fcf493b8b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237290"
---
# <a name="elements-xelement-dynamic-property"></a>Elements (XElement 動的プロパティ)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

現在の要素の子要素のうち指定された拡張名に一致する子要素の取得に使用するインデクサーを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
elem.Elements[{namespaceName}localName]   
```  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 `IEnumerable<XElement> Item(String expandedName)` 型のインデクサー。 このインデクサーは、目的の子要素の展開名を取得し、<xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` コレクション内の一致する子要素を返します。  
  
## <a name="remarks"></a>Remarks  
 このプロパティは、<xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> クラスの <xref:System.Xml.Linq.XContainer> メソッドに相当します。  
  
 返されるコレクション内の要素は、XML ソース ドキュメント順になります。  
  
 このプロパティは、遅延実行を使用します。  
  
## <a name="see-also"></a>関連項目  
 [XElement クラスの動的プロパティ](../designers/xelement-class-dynamic-properties.md)   
 [要素](../designers/element-xelement-dynamic-property.md)   
 [子孫](../designers/descendants-xelement-dynamic-property.md)



