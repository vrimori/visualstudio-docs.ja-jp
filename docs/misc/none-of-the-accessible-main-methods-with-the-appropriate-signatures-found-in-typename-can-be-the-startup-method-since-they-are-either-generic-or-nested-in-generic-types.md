---
title: "&#39;&lt;typename&gt;&#39; で見つかった正しいシグネチャを持つ、アクセス可能な &#39;Main&#39; メソッドは、いずれもスタートアップ メソッドにできません。これらはジェネリックであるか、ジェネリック型に入れ子にされています | Microsoft Docs"
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
  - "vbc30796"
  - "BC30796"
helpviewer_keywords: 
  - "BC30796"
ms.assetid: 606b3629-5a92-4c79-ace2-a530cab8c978
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; で見つかった正しいシグネチャを持つ、アクセス可能な &#39;Main&#39; メソッドは、いずれもスタートアップ メソッドにできません。これらはジェネリックであるか、ジェネリック型に入れ子にされています
クラス、モジュール、または構造体に、プロジェクトとしてスタートアップ プロシージャを修飾する `Main` プロシージャが含まれていません。  
  
 Visual Basic では、プロジェクトのスタートアップ プロシージャは型引数に依存しないようにする必要があります。 そのため、ジェネリックでもジェネリック型に含まれてもいない `Main` プロシージャに少なくとも 1 つアクセスできる必要があります。  
  
 **エラー ID:** BC30796  
  
### このエラーを解決するには  
  
-   少なくとも 1 つの `Main` プロシージャがジェネリックになることもジェネリック型に含まれることもないように定義します。  
  
     または  
  
-   プロジェクトの **\[プロパティ\]** ページで、**\[スタートアップ フォーム\]** または **\[スタートアップ オブジェクト\]** に別のフォームまたはモジュールを指定します。  
  
## 参照  
 [NIB 方法: プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NIB: Visual Basic バージョンの Hello World\!](http://msdn.microsoft.com/ja-jp/9d030b60-e148-4366-a462-69532f02294c)