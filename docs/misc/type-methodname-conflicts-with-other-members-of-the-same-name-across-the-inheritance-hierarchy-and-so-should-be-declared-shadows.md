---
title: "&lt;type&gt; &#39;&lt;methodname&gt;&#39; は、継承階層間で同じ名前の他のメンバーと競合しているため、&#39;Shadows&#39; と宣言しなければなりません | Microsoft Docs"
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
  - "vbc42000"
  - "bc42000"
helpviewer_keywords: 
  - "BC42000"
ms.assetid: 3081635f-99a9-4e90-997f-82251144d80f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type&gt; &#39;&lt;methodname&gt;&#39; は、継承階層間で同じ名前の他のメンバーと競合しているため、&#39;Shadows&#39; と宣言しなければなりません
2 つ以上のインターフェイスから継承するインターフェイスは、1 つ以上の基底インターフェイスで既に定義されているプロシージャと同じ名前を持つプロシージャを定義します。 このインターフェイスのプロシージャは、基底インターフェイスのプロシージャのいずれかをシャドウする必要があります。  
  
 このメッセージは警告です。`Shadows` は、既定で指定されていると見なされます。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42000  
  
### このエラーを解決するには  
  
-   基底インターフェイスのプロシージャのいずれかを隠ぺいする場合は、新しいプロシージャの宣言に `Shadows` キーワードを追加します。  
  
-   基底インターフェイスのプロシージャを隠ぺいしない場合は、新しいプロシージャの名前を変更します。  
  
## 参照  
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Shadowing in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)