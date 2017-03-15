---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; は、&#39;Public&#39; と宣言されていないため、&#39;&lt;classname&gt;&#39; に適用できません | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32509"
  - "vbc32509"
helpviewer_keywords: 
  - "BC32509"
ms.assetid: ac46851f-53ab-4ce6-87b1-4c4d29508527
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; は、&#39;Public&#39; と宣言されていないため、&#39;&lt;classname&gt;&#39; に適用できません
クラスが <xref:Microsoft.VisualBasic.ComClassAttribute> で宣言されていますが、その宣言で `Public` を指定していません。  
  
 COM 相互運用を使用できるようにするためには、.NET Framework クラスは次の要件を満たす必要があります。  
  
-   `Public` であり、そのすべてのコンテナーが `Public` であり、少なくとも 1 つの `Public` メンバーを公開している。  
  
-   *抽象クラス*ではない。つまり、`MustInherit` で宣言されていない。  
  
-   ジェネリックではない。またはジェネリック コンテナー型の中で宣言されていない。  
  
 **エラー ID:** BC32509  
  
### このエラーを解決するには  
  
-   `Public` キーワードをクラス宣言に追加します。  
  
     または  
  
-   クラスまたはそのコンテナー要素を `Public` にできない場合は、クラス宣言から <xref:Microsoft.VisualBasic.ComClassAttribute> を削除します。 このクラスは COM に公開できません。  
  
## 参照  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)