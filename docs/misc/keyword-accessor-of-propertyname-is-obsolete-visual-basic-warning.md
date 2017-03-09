---
title: "&#39;&lt;propertyname&gt;&#39; の &#39;&lt;keyword&gt;&#39; アクセサーは廃止されています (Visual Basic 警告)。 | Microsoft Docs"
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
  - "vbc40020"
  - "bc40020"
helpviewer_keywords: 
  - "BC40020"
ms.assetid: 005440f4-6e82-421c-b2ce-9c5139325bac
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;propertyname&gt;&#39; の &#39;&lt;keyword&gt;&#39; アクセサーは廃止されています (Visual Basic 警告)。
ステートメントにより、対応するプロシージャが <xref:System.ObsoleteAttribute> 属性および警告として扱うことを示すディレクティブでマークされた、プロパティの読み取りまたは書き込みが試行されます。  
  
 <xref:System.ObsoleteAttribute> を適用することで、使用されなくなった要素としてすべてのプログラミング要素にマークを付けることができます。 これを行う場合、この属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False` のどちらかに設定できます。`True` に設定した場合、コンパイラは、この要素を使用する試行をエラーとして処理します。`False` に設定するか、または既定の `False` にする場合、この要素の使用が試行されると、コンパイラは警告を発行します。  
  
 既定では、<xref:System.ObsoleteAttribute> の <xref:System.ObsoleteAttribute.IsError%2A> プロパティが `False` であるため、このメッセージは警告となります。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40020  
  
### このエラーを解決するには  
  
1.  ソース コードの参照で、プロパティ名のスペルが正しいことを確認してください。  
  
2.  このメッセージが生成された方法 \(読み取りまたは書き込み\) で、プロパティにアクセスしないようにします。  
  
## 参照  
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)