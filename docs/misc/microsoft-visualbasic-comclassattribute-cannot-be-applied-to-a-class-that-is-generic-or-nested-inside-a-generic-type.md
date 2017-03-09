---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; は、ジェネリック、またはジェネリック型の内部で入れ子になったクラスには適用できません。 | Microsoft Docs"
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
  - "vbc31527"
  - "bc31527"
helpviewer_keywords: 
  - "BC31527"
ms.assetid: ea125bff-d020-4933-b277-6e24943eea88
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; は、ジェネリック、またはジェネリック型の内部で入れ子になったクラスには適用できません。
クラスが <xref:Microsoft.VisualBasic.ComClassAttribute> で宣言されていますが、このクラスはジェネリックであるか、ジェネリック クラスまたは構造体に含まれています。  
  
 COM 相互運用を使用できるようにするためには、.NET Framework クラスは次の要件を満たす必要があります。  
  
-   `Public` であり、そのすべてのコンテナーが `Public` であり、少なくとも 1 つの `Public` メンバーを公開している。  
  
-   *抽象クラス*ではない。つまり、`MustInherit` で宣言されていない。  
  
-   ジェネリックではない。またはジェネリック コンテナー型の中で宣言されていない。  
  
 **エラー ID:** BC31527  
  
### このエラーを解決するには  
  
-   クラスの宣言を変更して、ジェネリックにならないようにします。さらに、そのクラスを含む要素がジェネリックでないようにします。  
  
     または  
  
-   クラスまたはそのクラスを含む要素をジェネリックにする必要がある場合は、クラスの宣言から <xref:Microsoft.VisualBasic.ComClassAttribute> を削除します。 このクラスは COM に公開できません。  
  
## 参照  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)