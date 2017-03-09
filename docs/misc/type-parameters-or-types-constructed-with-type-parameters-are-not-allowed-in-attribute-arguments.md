---
title: "型パラメーターまたは型パラメーターで構築された型は、属性の引数に許可されていません | Microsoft Docs"
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
  - "BC32079"
  - "vbc32079"
helpviewer_keywords: 
  - "BC32079"
ms.assetid: 93eb59bd-e7db-4f73-a37f-405a83df48c1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーターまたは型パラメーターで構築された型は、属性の引数に許可されていません
型パラメーターである引数、または型パラメーターを使用して構築された引数を使用して、属性が適用されています。  
  
 Visual Basic と .NET Framework は、属性とジェネリック型のどのような組み合わせも現在サポートしていません。 これは次の制限事項が適用されることを意味します。  
  
-   属性をジェネリック型とする、またはジェネリック型の中で宣言することはできません。  
  
-   属性は、ジェネリック クラスから継承できません。また、ジェネリック クラスは属性から継承できません。  
  
-   属性を適用するときに、次のいずれかである引数を指定することはできません。  
  
    -   ジェネリック型、  
  
    -   ジェネリック型から構築された型、  
  
    -   包含する型の型パラメーター、または  
  
    -   包含する型の型パラメーターから構築された型。  
  
 **エラー ID:** BC32079  
  
### このエラーを解決するには  
  
-   何らかの型パラメーター、または型パラメーターから構築された何らかの型が含まれないように、属性に指定された引数を再構築します。  
  
## 参照  
 <xref:System.Attribute>   
 [ビルド内にありません: Visual Basic での属性の概要](http://msdn.microsoft.com/ja-jp/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)