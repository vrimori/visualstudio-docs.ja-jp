---
title: XML (XElement 動的プロパティ) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74fdfa59e791fb8e0262df04b1e45f3b867fbd02
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537631"
---
# <a name="xml-xelement-dynamic-property"></a>XML (XElement 動的プロパティ)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Xml (XElement 動的プロパティ)](https://docs.microsoft.com/visualstudio/designers/xml-xelement-dynamic-property)します。  
  
要素について、書式設定されていない XML コンテンツを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 要素に関する書式設定されていない XML コンテンツを表す <xref:System.String>。  
  
## <a name="remarks"></a>Remarks  
 このプロパティは、<xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> パラメーターが <xref:System.Xml.Linq.XNode?displayProperty=fullName> に設定されている、`SaveOptions` クラスの <xref:System.Xml.Linq.SaveOptions> メソッドに相当します。  
  
## <a name="see-also"></a>関連項目  
 [XElement クラスの動的プロパティ](../designers/xelement-class-dynamic-properties.md)   
 [値](../designers/value-xelement-dynamic-property.md)



