---
title: "&#39;&lt;procedurename1&gt;&#39; は、このコンテキストではアクセスできないため、&#39;&lt;procedurename2&gt;&#39; でオーバーライドすることはできません。 | Microsoft Docs"
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
  - "bc31417"
  - "vbc31417"
helpviewer_keywords: 
  - "BC31417"
ms.assetid: 1a36acbf-cead-43a0-b12f-f52f94d09124
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;procedurename1&gt;&#39; は、このコンテキストではアクセスできないため、&#39;&lt;procedurename2&gt;&#39; でオーバーライドすることはできません。
プロシージャまたはプロパティが別のプロシージャまたはプロパティをオーバーライドしますが、前者からのアクセスを禁ずるアクセス レベルが後者に設定されています。  
  
 たとえば、あるアセンブリで `Friend` と宣言されているプロシージャには、そのアセンブリの外部でアクセスできません。 同じプロジェクト内の別のアセンブリに含まれているあるプロシージャが `Friend` プロシージャをオーバーライドしようとする場合、これにアクセスしてオーバーライドすることはできません。  
  
 **エラー ID:** BC31417  
  
### このエラーを解決するには  
  
-   オーバーライドするプロシージャまたはプロパティを、オーバーライド先のプロシージャまたはプロパティと同じアセンブリに移動します。  
  
     または  
  
-   `Overrides` キーワードを削除します。  
  
## 参照  
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [ビルド内にありません: プロパティとメソッドのオーバーライド](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)