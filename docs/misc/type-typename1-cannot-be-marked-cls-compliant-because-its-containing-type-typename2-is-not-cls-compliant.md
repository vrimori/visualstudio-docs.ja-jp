---
title: "CLS に準拠していない型 &#39;&lt;typename2&gt;&#39; を含んでいるため、型 &#39;&lt;typename1&gt;&#39; を CLS 準拠として設定できません。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40030"
  - "bc40030"
helpviewer_keywords: 
  - "BC40030"
ms.assetid: f1cfcf04-2a99-46ef-ac87-34cc2099125c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CLS に準拠していない型 &#39;&lt;typename2&gt;&#39; を含んでいるため、型 &#39;&lt;typename1&gt;&#39; を CLS 準拠として設定できません。
クラスまたはインターフェイスが、`<CLSCompliant(False)>` としてマークされている型に入れ子になっているか、またはマークされていないときに、`<CLSCompliant(True)>` としてマークされています。  
  
 クラスまたはインターフェイスが [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) に準拠するためには、そのコンテインメント階層全体が準拠している必要があります。 つまり、入れ子になったすべての型が準拠している必要があります。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 <xref:System.CLSCompliantAttribute> を要素に適用しなかった場合は、非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40030  
  
### このエラーを解決するには  
  
-   CLS 準拠を必要とする場合は、別のコンテインメント階層内にこの型を定義します。  
  
-   この型を現在のコンテインメント階層内に残すことが必要な場合は、<xref:System.CLSCompliantAttribute> をその定義から削除するか、または `<CLSCompliant(False)>` としてマークします。  
  
## 参照  
 [\<PAVE OVER\> CLS準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)