---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; を、&#39;MustInherit&#39; に宣言されているクラスに適用することはできません | Microsoft Docs"
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
  - "BC32508"
  - "vbc32508"
helpviewer_keywords: 
  - "BC32508"
ms.assetid: c8af606d-f448-4703-98df-e594fd511f92
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; を、&#39;MustInherit&#39; に宣言されているクラスに適用することはできません
クラスが <xref:Microsoft.VisualBasic.ComClassAttribute> で宣言されていますが、その宣言で `MustInherit` を指定しています。  
  
 COM 相互運用を使用できるようにするためには、.NET Framework クラスは次の要件を満たす必要があります。  
  
-   `Public` であり、そのすべてのコンテナーが `Public` であり、少なくとも 1 つの `Public` メンバーを公開している。  
  
-   *抽象クラス*ではない。つまり、`MustInherit` で宣言されていない。  
  
-   ジェネリックではない。またはジェネリック コンテナー型の中で宣言されていない。  
  
 **エラー ID:** BC32508  
  
### このエラーを解決するには  
  
-   クラス宣言から `MustInherit` キーワードを削除します。  
  
     または  
  
-   クラスまたはそのコンテナー要素をジェネリックにする必要がある場合は、クラスの宣言から <xref:Microsoft.VisualBasic.ComClassAttribute> を削除します。 このクラスは COM に公開できません。  
  
## 参照  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)