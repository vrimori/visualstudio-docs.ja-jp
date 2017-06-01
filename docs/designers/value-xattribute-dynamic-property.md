---
title: "Value (XAttribute 動的プロパティ) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c013001a52e5b894bcbcdaf9a40309505b39140c
ms.contentlocale: ja-jp
ms.lasthandoff: 05/19/2017

---
# <a name="value-xattribute-dynamic-property"></a>Value (XAttribute 動的プロパティ)
XML 属性の値を取得または設定します。  
  
## <a name="syntax"></a>構文  
  
```  
attrib.Value   
```  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 この属性の値を表す <xref:System.String> です。  
  
## <a name="exceptions"></a>例外  
  
|例外の種類|状態|  
|--------------------|---------------|  
|<xref:System.ArgumentNullException>|設定時に `value` が `null` である場合に発生します。|  
  
## <a name="remarks"></a>コメント  
 このプロパティは、<xref:System.Xml.Linq.XAttribute.Value%2A> クラスの <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> プロパティに相当します。ただし、この動的プロパティは変更通知もサポートします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [XAttribute クラスの動的プロパティ](../designers/xattribute-class-dynamic-properties.md)   
 [属性](../designers/attribute-xelement-dynamic-property.md)
