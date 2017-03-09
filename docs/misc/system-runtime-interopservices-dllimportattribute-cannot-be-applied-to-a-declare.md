---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; は Declare に適用できません | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31523"
  - "vbc31523"
helpviewer_keywords: 
  - "BC31523"
ms.assetid: 04c8a14f-9286-4f9a-aad5-a0555e5f09f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; は Declare に適用できません
`DllImportAttribute` 属性が `Declare` 関数に適用されました。 この属性は、空の `Function` または `Sub` でのみ使用できます。  
  
 **エラー ID:** BC31523  
  
### このエラーを解決するには  
  
1.  `Declare` ステートメントから `DllImportAttribute` 属性を削除します。  
  
## 参照  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement)