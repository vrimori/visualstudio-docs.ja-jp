---
title: "ジェネリック、またはジェネリック型に含まれるクラスは、属性クラスから継承できません | Microsoft Docs"
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
  - "vbc32074"
  - "BC32074"
helpviewer_keywords: 
  - "BC32074"
ms.assetid: 3552ac98-d86a-4962-9d51-b9a8acc38ea1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ジェネリック、またはジェネリック型に含まれるクラスは、属性クラスから継承できません
ジェネリック クラスまたはジェネリック型の中で入れ子になったクラスで、属性クラスから継承すると指定されています。  
  
 Visual Basic と .NET Framework は、属性とジェネリック型の任意の組み合わせを現在サポートしていません。 これは次の制限事項が適用されることを意味します。  
  
-   属性をジェネリック型とする、またはジェネリック型の中で宣言することはできません。  
  
-   属性は、ジェネリック クラスから継承できません。また、ジェネリック クラスは属性から継承できません。  
  
-   属性を適用する場合は、次のいずれかである引数を指定することはできません。  
  
    -   ジェネリック型、  
  
    -   ジェネリック型から構築された型、  
  
    -   包含する型の型パラメーター、または  
  
    -   包含する型の型パラメーターから構築された型。  
  
 **エラー ID:** BC32074  
  
### このエラーを解決するには  
  
-   基底クラスを属性クラス以外のものに変更するか、`Inherits` ステートメントを完全に削除します。  
  
## 参照  
 <xref:System.Attribute>   
 [ビルド内にありません: Visual Basic における属性](http://msdn.microsoft.com/ja-jp/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)