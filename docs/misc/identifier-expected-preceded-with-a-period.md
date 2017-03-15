---
title: "前にピリオドが付いた識別子が必要です。 | Microsoft Docs"
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
  - "bc36576"
  - "vbc36576"
helpviewer_keywords: 
  - "BC36576"
ms.assetid: 02217cc4-8972-4a6d-97a6-4ecbb7399af2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 前にピリオドが付いた識別子が必要です。
プロパティ名を推論できない値が、プロパティ名に割り当てられることなく、匿名型の宣言の初期化子リストに含まれています。  
  
```  
' Not valid. ' Dim anon1 = New With {.grade = 100, 95}  
```  
  
 **エラー ID:** BC36576  
  
### このエラーを解決するには  
  
-   次のコードに示すように、初期化子リスト内の各値にプロパティ名を指定します。  
  
    ```  
    Dim anon2 = New With {.grade1 = 100, .grade2 = 95}  
    ```  
  
## 参照  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [方法: 匿名型のインスタンスを宣言する \(Visual Basic\)。](http://msdn.microsoft.com/ja-jp/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)