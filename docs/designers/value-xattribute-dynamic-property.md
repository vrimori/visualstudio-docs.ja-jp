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
ms.workload: multiple
ms.openlocfilehash: 4807a84b9e1de5186e72cbe138f0f54e2f33525e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
|例外の種類|条件|  
|--------------------|---------------|  
|<xref:System.ArgumentNullException>|設定時に `value` が `null` である場合に発生します。|  
  
## <a name="remarks"></a>コメント  
 このプロパティは、<xref:System.Xml.Linq.XAttribute.Value%2A> クラスの <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> プロパティに相当します。ただし、この動的プロパティは変更通知もサポートします。  
  
## <a name="see-also"></a>参照  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [XAttribute クラスの動的プロパティ](../designers/xattribute-class-dynamic-properties.md)   
 [属性](../designers/attribute-xelement-dynamic-property.md)