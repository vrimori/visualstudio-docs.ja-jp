---
title: "メンバー &#39;&lt;membername1&gt;&#39; が、基底クラス &#39;&lt;baseclassname&gt;&#39; のメンバー と競合する &#39;&lt;implicitmembername&gt;&#39; を暗黙的に宣言しています | Microsoft Docs"
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
  - "vbc40022"
  - "bc40022"
helpviewer_keywords: 
  - "BC40022"
ms.assetid: be5bb2ee-2274-42b2-b843-179b14127b34
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メンバー &#39;&lt;membername1&gt;&#39; が、基底クラス &#39;&lt;baseclassname&gt;&#39; のメンバー と競合する &#39;&lt;implicitmembername&gt;&#39; を暗黙的に宣言しています
メンバー '\<membername1\>' が、基底クラス '\<baseclassname\>' のメンバー と競合する '\<implicitmembername\>' を暗黙的に宣言しているため、このメンバーを 'Overloads' として宣言できません  
  
 派生クラスのプロパティが、基底クラスのメンバーと同じ名前を持つ暗黙的なメンバーを生成し、[Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) キーワードを指定しています。  
  
 オーバーロードが、すべて同じクラス内にある、複数のバージョンのプロパティまたはプロシージャを定義するために使用されています。 基底クラスのメンバーが既に `Overloads` を指定しているのでない限り、追加バージョンの基底クラスのメンバーは定義できません。 競合している既定クラスのメンバーは `Overloads` を指定しないので、コンパイラはこのプロパティ [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) を暗黙的な基底クラスのメンバーとみなします。  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラは、宣言されている特定のプログラミング要素に対応する暗黙的なメンバーを作成します。 次の表には、これらの暗黙なメンバー、つまり*統合*メンバーをまとめています。  
  
|宣言された要素|暗黙的に作成されるメンバー|  
|-------------|-------------------|  
|列挙型|`value__` のメンバー|  
|イベント|`add_<eventname>` プロシージャ<br /><br /> `remove_<eventname>` プロシージャ<br /><br /> `<eventname>Event` のフィールド<br /><br /> `<eventname>EventHandler` デリゲート|  
|プロパティ|`get_<propertyname>` プロシージャ<br /><br /> `set_<propertyname>` プロシージャ|  
|`My.Form` メンバー、`My.WebService` メンバー、または <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute> 属性でマークされたクラスのメンバー|`m_<variablename>` `Static` 変数<br /><br /> `<variablename>` プロパティ<br /><br /> `get_<variablename>` プロシージャ<br /><br /> `set_<variablename>` プロシージャ|  
|`WithEvents` 変数|`_<variablename>` 変数<br /><br /> `<variablename>` プロパティ<br /><br /> `get_<variablename>` プロシージャ<br /><br /> `set_<variablename>` プロシージャ|  
  
 名前競合のリスクがあるため、これらの暗黙的なメンバーのいずれかと同じ形式を使用して、宣言されたプログラミング要素に名前を付けることは避ける必要があります。 たとえば、`get_` または `set_` で始まる要素名を避ける必要があります。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」をご覧ください。  
  
 **エラー ID:** BC40022  
  
### このエラーを解決するには  
  
-   基底クラスのメンバーを非表示、つまりシャドウする場合は、プロパティの宣言内で、[Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) キーワードを [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) キーワードに置き換えます。  
  
-   基底クラスのメンバーをシャドウしない場合は、上の表で説明されている名前との競合を避けるために、プロパティの名前を変更します。  
  
## 参照  
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)