---
title: "属性をジェネリック、またはジェネリック内部で入れ子になった型にすることはできません | Microsoft Docs"
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
  - "bc32067"
  - "vbc32067"
helpviewer_keywords: 
  - "BC32067"
ms.assetid: 93ae2848-0a72-4ae5-82a3-32e0a49bb7cd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 属性をジェネリック、またはジェネリック内部で入れ子になった型にすることはできません
属性が、ジェネリック型として、またはジェネリック型の中で宣言されています。  
  
 Visual Basic と .NET Framework は、属性とジェネリック型のどのような組み合わせも現在サポートしていません。 これは次の制限事項が適用されることを意味します。  
  
-   属性をジェネリック型とする、またはジェネリック型の中で宣言することはできません。  
  
-   属性は、ジェネリック クラスから継承できません。また、ジェネリック クラスは属性から継承できません。  
  
-   属性を適用するときに、次のいずれかである引数を指定することはできません。  
  
    -   ジェネリック型、  
  
    -   ジェネリック型から構築された型、  
  
    -   包含する型の型パラメーター、または  
  
    -   包含する型の型パラメーターから構築された型。  
  
 **エラー ID:** BC32067  
  
### このエラーを解決するには  
  
-   属性の宣言に `Of` キーワードと型パラメーター リストが含まれている場合、それらを削除します。  
  
-   属性の宣言がジェネリック型の内部にある場合、いずれのジェネリック型の内部でもない場所へ移動します。  
  
## 参照  
 <xref:System.Attribute>   
 [ビルド内にありません: Visual Basic での属性の概要](http://msdn.microsoft.com/ja-jp/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)