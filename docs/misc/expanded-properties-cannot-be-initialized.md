---
title: "展開されたプロパティは初期化できません | Microsoft Docs"
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
  - "vbc36714"
  - "bc36714"
helpviewer_keywords: 
  - "BC36714"
ms.assetid: ba9408f3-e606-4749-8372-987999f405f5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 展開されたプロパティは初期化できません
自動実装プロパティは宣言の一部として初期化できますが、展開されたプロパティは初期化できません。  
  
 **エラー ID:** BC36714  
  
### このエラーを解決するには  
  
-   自動実装プロパティを使用するか、プロパティ宣言から初期化を削除します。  
  
## 使用例  
 次の例では、自動実装プロパティと展開されたプロパティの両方を示します。 自動実装プロパティは、割り当てを使用するか `New` 句を使用して初期化できますが、展開されたプロパティは初期化できません。  
  
```vb#  
Class AutoImplementedExample ' An auto-implemented property can be assigned an initial value. Property IDNum As Integer = 33542 ' An auto-implemented property can be initialized with New. Property Name As New String("Don Hall") End Class Class ExpandedExample ' Attempting to expand an initialized auto-implemented property ' causes this error. 'Property IDNum As Integer = 33542 '    Get '    End Get '    Set(ByVal value As Integer) '    End Set 'End Property ' Instead, you can assign the initial value to the backing field. Private _IDNum As Integer = 33542 Property IDNum As Integer Get End Get Set(ByVal value As Integer) End Set End Property End Class  
```  
  
## 参照  
 [Auto\-Implemented Properties](/dotnet/visual-basic/programming-guide/language-features/procedures/auto-implemented-properties)   
 [How to: Create a Property](../Topic/How%20to:%20Create%20a%20Property%20\(Visual%20Basic\).md)   
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)