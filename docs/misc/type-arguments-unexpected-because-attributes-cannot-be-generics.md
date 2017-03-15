---
title: "属性を汎用にできないため、予期しない型引数です | Microsoft Docs"
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
  - "bc32066"
  - "vbc32066"
helpviewer_keywords: 
  - "BC32066"
ms.assetid: cd43a92c-33fb-4def-bbf7-527d21bff93c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 属性を汎用にできないため、予期しない型引数です
型引数リストを使用して、属性が適用されます。  
  
 Visual Basic と .NET Framework は、属性とジェネリック型の任意の組み合わせを現在サポートしていません。 これは次の制限事項が適用されることを意味します。  
  
-   属性をジェネリック型とする、またはジェネリック型の中で宣言することはできません。  
  
-   属性は、ジェネリック クラスから継承できません。また、ジェネリック クラスは属性から継承できません。  
  
-   属性を適用する場合は、次のいずれかである引数を指定することはできません。  
  
    -   ジェネリック型、  
  
    -   ジェネリック型から構築された型、  
  
    -   包含する型の型パラメーター、または  
  
    -   包含する型の型パラメーターから構築された型。  
  
 **エラー ID:** BC32066  
  
### このエラーを解決するには  
  
-   型引数が標準的な引数であることを想定している場合は、`Of` キーワードを削除します。 これにより、型引数リストが標準的な引数リストになります。  
  
-   型引数が型パラメーターに指定されることが想定される場合は、`Of` キーワードとすべての型引数を削除します。 属性は、型引数を受け入れることはできません。  
  
## 参照  
 <xref:System.Attribute>   
 [ビルド内にありません: Visual Basic における属性](http://msdn.microsoft.com/ja-jp/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)