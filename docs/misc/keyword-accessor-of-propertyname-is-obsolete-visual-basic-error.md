---
title: "&#39;&lt;propertyname&gt;&#39; の &#39;&lt;keyword&gt;&#39; アクセサーは廃止されています (Visual Basic エラー) | Microsoft Docs"
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
  - "vbc30912"
  - "bc30912"
helpviewer_keywords: 
  - "BC30912"
ms.assetid: f1fa965e-090c-49f3-ab1e-cbb2f9b2a5f0
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;propertyname&gt;&#39; の &#39;&lt;keyword&gt;&#39; アクセサーは廃止されています (Visual Basic エラー)
ステートメントにより、対応するプロシージャが <xref:System.ObsoleteAttribute> 属性およびエラーとして扱うことを示すディレクティブでマークされた、プロパティの読み取りまたは書き込みが試行されます。  
  
 <xref:System.ObsoleteAttribute> を適用することで、使用されなくなった要素としてすべてのプログラミング要素にマークを付けることができます。 これを行う場合、この属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False` のどちらかに設定できます。`True` に設定した場合、コンパイラは、この要素を使用する試行をエラーとして処理します。`False` に設定するか、または既定の `False` にする場合、この要素の使用が試行されると、コンパイラは警告を発行します。  
  
 **エラー ID:** BC30912  
  
### このエラーを解決するには  
  
1.  ソース コードの参照で、プロパティ名のスペルが正しいことを確認してください。  
  
2.  このメッセージが生成される方法 \(読み取りまたは書き込み\) で、プロパティにアクセスしないようにします。  
  
## 参照  
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)