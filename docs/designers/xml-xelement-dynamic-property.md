---
title: "XML (XElement 動的プロパティ) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b03c03ce5980b1c6042d1670d33d43fea6c7edc4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [XElement クラスの動的プロパティ](../designers/xelement-class-dynamic-properties.md)   
 [値](../designers/value-xelement-dynamic-property.md)