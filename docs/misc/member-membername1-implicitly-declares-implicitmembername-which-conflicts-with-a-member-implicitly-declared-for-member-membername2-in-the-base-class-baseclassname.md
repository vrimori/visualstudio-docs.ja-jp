---
title: "メンバー &#39;&lt;membername1&gt;&#39; は、ベース クラス &#39;&lt;baseclassname&gt;&#39; でメンバー &#39;&lt;membername2&gt;&#39; に対して暗黙的に宣言されたメンバーと競合する &#39;&lt;implicitmembername&gt;&#39; を暗黙的に宣言します | Microsoft Docs"
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
  - "vbc40018"
  - "bc40018"
helpviewer_keywords: 
  - "BC40018"
ms.assetid: 43844e55-9ce1-4b88-9aa8-839b37f30e5a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メンバー &#39;&lt;membername1&gt;&#39; は、ベース クラス &#39;&lt;baseclassname&gt;&#39; でメンバー &#39;&lt;membername2&gt;&#39; に対して暗黙的に宣言されたメンバーと競合する &#39;&lt;implicitmembername&gt;&#39; を暗黙的に宣言します
メンバー '\<membername1\>' は、基底クラス '\<baseclassname\>' のメンバー '\<membername2\>' に対して暗黙的に宣言されているメンバーと競合する '\<implicitmembername\>' を暗黙的に宣言しています。 そのため、このメンバーを 'Shadows' であると宣言する必要があります。  
  
 派生クラスのメンバーが、基底クラスの暗黙的なメンバーと同じ名前を持つ暗黙的なメンバーを生成しています。 暗黙的なメンバーは [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) を指定しないため、コンパイラはこのメンバーが暗黙的な基底クラスのメンバーをシャドウ \([Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)\) していると見なします。 このメンバーに `Shadows` キーワードを明示的に指定すると、コードが読みやすくなり、エラーが発生しにくくなります。  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラは、宣言されている特定のプログラミング要素に対応する暗黙的なメンバーを作成します。 これらの暗黙的なメンバー、つまり*合成*メンバーの概要を次の表に示します。  
  
|宣言された要素|暗黙的に作成されるメンバー|  
|-------------|-------------------|  
|列挙型|`value__` のメンバー|  
|イベント|`add_<eventname>` プロシージャ<br /><br /> `remove_<eventname>` プロシージャ<br /><br /> `<eventname>Event` のフィールド<br /><br /> `<eventname>EventHandler` デリゲート|  
|プロパティ|`get_<propertyname>` プロシージャ<br /><br /> `set_<propertyname>` プロシージャ|  
|`My.Form` メンバー、`My.WebService` メンバー、または <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute> 属性でマークされたクラスのメンバー|`m_<variablename>` `Static` 変数<br /><br /> `<variablename>` プロパティ<br /><br /> `get_<variablename>` プロシージャ<br /><br /> `set_<variablename>` プロシージャ|  
|`WithEvents` 変数|`_<variablename>` 変数<br /><br /> `<variablename>` プロパティ<br /><br /> `get_<variablename>` プロシージャ<br /><br /> `set_<variablename>` プロシージャ|  
  
 名前競合のリスクがあるため、宣言するプログラミング要素に名前を付ける場合は、これらの暗黙的なメンバーのいずれかと同じ形式を使用することは避ける必要があります。 たとえば、`get_` または `set_` で始まる要素名を避ける必要があります。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40018  
  
### このエラーを解決するには  
  
-   暗黙的な基底クラスのメンバーを隠す、つまりシャドウする場合は、派生クラスのメンバーの宣言に [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) キーワードを含めます。  
  
-   暗黙的な基底クラスのメンバーをシャドウしない場合は、前の表に示した名前との競合を避けるために、派生クラスのメンバーの名前を変更します。  
  
## 参照  
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)