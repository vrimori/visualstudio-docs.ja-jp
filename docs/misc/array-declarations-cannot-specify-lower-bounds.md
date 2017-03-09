---
title: "配列宣言で下限を指定することはできません | Microsoft Docs"
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
  - "vbc30805"
  - "bc30805"
helpviewer_keywords: 
  - "BC30805"
ms.assetid: f2055387-f4dc-4366-89fb-d752929a0258
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 配列宣言で下限を指定することはできません
配列の下限は常に 0 です。 コードを読みやすくするための下限として 0 を指定することができます。 ただし、下限としてその他の値を指定できません。  
  
 **エラー ID:** BC30805  
  
### このエラーを解決するには  
  
-   配列の次元を要素の総数よりも 1 小さい値に設定します。 たとえば、`Dim y(6)` と `Dim x(3 To 9)` のサイズは同じです \(7 つの要素\)。`Dim y(0 To 6)` を指定することもできます。  
  
-   オフセットを使用して、0 以外の下限をシミュレートします。 次の例では、次元を 3 から 9 に設定した配列をシミュレートします。  
  
    ```  
    Const offset As Integer = 3 Dim arrayIndex As Integer ' arrayIndex can vary between 3 and 9. Dim y(0 To 6) ' The preceding statement allocates the same number of elements ' as Dim y(3 To 9). y(arrayIndex - offset) = value ' The preceding statement converts arrayIndex to the ' corresponding index of y.  
    ```  
  
## 参照  
 [配列](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [Array Dimensions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/array-dimensions)   
 [NOTINBUILD 方法: 配列の下限値に 0 を指定する](http://msdn.microsoft.com/ja-jp/20ffd49a-64f7-4634-8ed0-46ba1049d935)