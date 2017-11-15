---
title: "Value (XAttribute 動的プロパティ) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7d647e7623820c6621f6605277a695a98454fec5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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