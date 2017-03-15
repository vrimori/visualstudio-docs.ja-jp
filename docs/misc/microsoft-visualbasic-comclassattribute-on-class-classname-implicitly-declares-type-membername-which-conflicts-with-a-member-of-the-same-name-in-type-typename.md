---
title: "&#39;&lt;classname&gt;&#39; の &#39;Microsoft.VisualBasic.ComClassAttribute&#39; は、&lt;type&gt; &#39;&lt;typename&gt;&#39; にある同じ名前のメンバーと競合する &lt;type&gt; &#39;&lt;membername&gt;&#39; を暗黙的に宣言します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BC42101"
ms.assetid: 001c8eaa-19b6-44fa-8056-4186ecffbda8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;classname&gt;&#39; の &#39;Microsoft.VisualBasic.ComClassAttribute&#39; は、&lt;type&gt; &#39;&lt;typename&gt;&#39; にある同じ名前のメンバーと競合する &lt;type&gt; &#39;&lt;membername&gt;&#39; を暗黙的に宣言します。
'\<classname\>' の 'Microsoft.VisualBasic.ComClassAttribute' は、\<type\> '\<typename\>' にある同じ名前のメンバーと競合する \<type\> '\<membername\>' を暗黙的に宣言します。 ベース '\<typename\>' の名前を非表示にする場合は 'Microsoft.VisualBasic.ComClassAttribute\(InterfaceShadows:\=True\)' に設定してください。  
  
 クラスで `COMClassAttribute` 属性ブロックを使用して、基底クラスのメンバーと同じ名前のインターフェイスを暗黙的に定義します。 このような場合、インターフェイス名により、基底クラスのメンバーをシャドウする必要があります。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42101  
  
### このエラーを解決するには  
  
1.  基底クラスのメンバーを非表示にする場合は、`ComClassAttribute` 属性ブロックで `InterfaceShadows:=True` を設定します。  
  
2.  基底クラスのメンバーを非表示にしない場合は、クラスの名前を変更します。  
  
## 参照  
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute クラス](http://msdn.microsoft.com/ja-jp/5c2f0835-9210-47dc-bc59-5c1769953574)   
 [ComClassAttribute.InterfaceShadows プロパティ](http://msdn.microsoft.com/ja-jp/0fae25bd-e0ba-4755-a76c-3b526b1ac795)