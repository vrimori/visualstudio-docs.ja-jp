---
title: "&#39;&lt;elementname&gt;&#39; は古い形式です: &#39;&lt;errormessage&gt;&#39; | Microsoft Docs"
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
  - "bc40000"
  - "vbc40000"
helpviewer_keywords: 
  - "BC40000"
ms.assetid: dade0f57-eca1-4dd0-b978-020678838be6
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;elementname&gt;&#39; は古い形式です: &#39;&lt;errormessage&gt;&#39;
<xref:System.ObsoleteAttribute> 属性でマークされているプログラミング要素にステートメントがアクセスを試行しています。この試行をディレクティブは警告として処理します。  
  
 <xref:System.ObsoleteAttribute> を適用することで、任意のプログラミング要素を使用しない要素としてマークできます。 これを行う場合は、属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False` に設定できます。`True` に設定した場合、コンパイラは要素を使用する試行をエラーとして処理します。`False` に設定した場合や既定値の `False` を使用した場合、コンパイラは要素の使用が試行されると警告を発行します。  
  
 既定では、<xref:System.ObsoleteAttribute> の <xref:System.ObsoleteAttribute.IsError%2A> プロパティが `False` であるため、このメッセージは警告になります。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40000  
  
### このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを確認し、適切なアクションを実行します。  
  
2.  ソース コード参照の要素名のスペルが正しいことを確認します。  
  
## 参照  
 [NOT IN BUILD: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)