---
title: "XML (XElement 動的プロパティ) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
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
ms.openlocfilehash: 3bd6e84a3e59033aeb5050c172439bccbd096082
ms.lasthandoff: 02/22/2017

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
 このプロパティは、`SaveOptions` パラメーターを <xref:System.Xml.Linq.SaveOptions> に設定した、<xref:System.Xml.Linq.XNode?displayProperty=fullName> クラスの <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> メソッドに等しくなります。  
  
## <a name="see-also"></a>関連項目  
 [XElement クラスの動的プロパティ](../designers/xelement-class-dynamic-properties.md)   
 [値](../designers/value-xelement-dynamic-property.md)
