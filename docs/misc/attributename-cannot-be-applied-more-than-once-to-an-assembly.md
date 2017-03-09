---
title: "&#39;&lt;attributename&gt;&#39; をアセンブリに 2 回以上適用することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31521"
  - "vbc31521"
helpviewer_keywords: 
  - "BC31521"
ms.assetid: 7312570f-8afb-4afe-992f-b6f7796f5f26
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;attributename&gt;&#39; をアセンブリに 2 回以上適用することはできません
指定した属性は、1 つの属性に 1 回のみ適用できます。  
  
 **エラー ID:** BC31521  
  
### このエラーを解決するには  
  
1.  この属性の重複するアプリケーションを削除します。  
  
2.  独自に開発したカスタム属性を使用している場合は、`AttributeUsageAttribute` を変更し、`AllowMultiple` プロパティを `True` に設定します。  
  
## 参照  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=fullName>