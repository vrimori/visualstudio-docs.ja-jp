---
title: "名前 &#39;&lt;name&gt;&#39; は宣言されていないか、または現在のスコープ内に存在しません。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36610"
  - "bc36610"
helpviewer_keywords: 
  - "BC36610"
ms.assetid: e66a4b8a-9252-42ae-a30d-341fad4f74be
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 名前 &#39;&lt;name&gt;&#39; は宣言されていないか、または現在のスコープ内に存在しません。
LINQ クエリでプログラミング要素を参照していますが、指定された名前に完全に一致する要素をコンパイラが見つけることができません。  
  
 **エラー ID:** BC36610  
  
### このエラーを解決するには  
  
1.  参照元のステートメントで名前のスペルを確認します。[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] は、大文字と小文字を区別しませんが、スペルにその他の違いがあった場合には異なる名前であると見なします。 アンダースコア \(`_`\) も名前の一部であり、スペルに含まれます。  
  
2.  プログラミング要素が範囲内にあることを確認します。 参照元のステートメントがプログラミング要素を宣言している領域の外部にある場合は、要素名を修飾する必要がある場合があります。 詳細については、「[Scope in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/scope)」を参照してください。  
  
3.  オブジェクトとメンバーの間にメンバー アクセス演算子 \(`.`\) を指定していることを確認します。 たとえば、`TextBox1` という名前の <xref:System.Windows.Forms.TextBox> コントロールがある場合、このコントロールの <xref:System.Windows.Forms.TextBoxBase.Text%2A> プロパティにアクセスするには、「`TextBox1.Text`」と入力する必要があります。 代わりに「`TextBox1Text`」と入力した場合、別の名前と見なされます。  
  
## 参照  
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Visual Basic Naming Conventions](/dotnet/visual-basic/programming-guide/program-structure/naming-conventions)   
 [References to Declared Elements](/dotnet/visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements)