---
title: "Elements (XElement 動的プロパティ) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 2
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 24dc395f229ae79696df926630c7e72b5ad1672d
ms.lasthandoff: 02/22/2017

---
# <a name="elements-xelement-dynamic-property"></a>Elements (XElement 動的プロパティ)
現在の要素の子要素のうち指定された拡張名に一致する子要素の取得に使用するインデクサーを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
elem.Elements[{namespaceName}localName]   
```  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 `IEnumerable<XElement> Item(String expandedName)` 型のインデクサー。 このインデクサーは、目的の子要素の展開名を取得し、<xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` コレクション内の一致する子要素を返します。  
  
## <a name="remarks"></a>コメント  
 このプロパティは、<xref:System.Xml.Linq.XContainer> クラスの <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> メソッドに相当します。  
  
 返されるコレクション内の要素は、XML ソース ドキュメント順になります。  
  
 このプロパティは、遅延実行を使用します。  
  
## <a name="see-also"></a>関連項目  
 [XElement クラスの動的プロパティ](../designers/xelement-class-dynamic-properties.md)   
 [要素](../designers/element-xelement-dynamic-property.md)   
 [子孫](../designers/descendants-xelement-dynamic-property.md)
