---
title: "未使用のローカル変数: &#39;&lt;localvariablename&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42024"
  - "BC42024"
helpviewer_keywords: 
  - "BC42024"
ms.assetid: 749b1315-0f85-4f7e-b68b-8cc4346c502b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 未使用のローカル変数: &#39;&lt;localvariablename&gt;&#39;
プロシージャでローカル変数が宣言されているが、使用されていません。  
  
 プロシージャのローカル変数間にスペル ミスがある可能性があります。 この変数は実際には別のステートメントで使用されているが、スペルが間違っているという場合、コンパイラは 2 つの異なる変数であると見なします。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42024  
  
### このエラーを解決するには  
  
1.  プロシージャ内のローカル変数間にスペル ミスがないかどうかを確認します。 大文字と小文字を区別しても、違うことにはならないので注意してください。 名前 `ABC` と `abc` は同じ変数を示していると見なされます。  
  
2.  スペル ミスがない場合は、この変数の宣言を削除するか、プロシージャ内の別のステートメントで使用します。  
  
## 参照  
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)