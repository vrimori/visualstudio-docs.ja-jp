---
title: "型の制約を &#39;NotInheritable&#39; クラスに指定することはできません | Microsoft Docs"
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
  - "vbc32060"
  - "bc32060"
helpviewer_keywords: 
  - "BC32060"
ms.assetid: f45cc0b6-7df1-462a-b3df-c526c143e16a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型の制約を &#39;NotInheritable&#39; クラスに指定することはできません
制約リストに [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable) としてマークされているクラスが含まれています。  
  
 型パラメーターの制約リストは、最大 1 つのクラスを受け入れることができます。 その型パラメーターに指定された型引数は、そのクラスから継承する必要があります。 そのため、型パラメーターは、*シール* つまり `NotInheritable` のクラスを制約として受け入れることはできません。  
  
 **エラー ID:** BC32060  
  
### このエラーを解決するには  
  
-   型パラメーターがクラスから継承できる必要があり、クラスの定義に制御を持っている場合、クラスから `NotInheritable` 宣言を削除します。  
  
-   クラスが `NotInheritable` のままである必要がある場合は、制約として使用することはできません。 制約リストから、クラス名を削除します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)