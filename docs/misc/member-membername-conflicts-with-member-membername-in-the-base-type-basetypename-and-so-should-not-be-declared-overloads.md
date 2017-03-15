---
title: "メンバー &#39;&lt;membername&gt;&#39; は、基本データ型 &#39;&lt;basetypename&gt;&#39; 内のメンバー &#39;&lt;membername&gt;&#39; と競合するため、&#39;Overloads&#39; として宣言できません | Microsoft Docs"
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
  - "bc40021"
  - "vbc40021"
helpviewer_keywords: 
  - "BC40021"
ms.assetid: 2ec72726-ab0e-4545-9c1e-2409eb54482e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メンバー &#39;&lt;membername&gt;&#39; は、基本データ型 &#39;&lt;basetypename&gt;&#39; 内のメンバー &#39;&lt;membername&gt;&#39; と競合するため、&#39;Overloads&#39; として宣言できません
プロパティまたはプロシージャが、同じ名前を持つ既存のプロパティまたはプロシージャを再宣言するために [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) キーワードを使用していますが、既存のプロパティまたはプロシージャは基底クラスに存在しています。  
  
 オーバーロードは、すべて同じクラス内にある、複数のバージョンのプロパティまたはプロシージャを定義するために使用されます。 基底クラスのメンバーが既に [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) を指定しているのでなければ、基底クラスのメンバーの追加バージョンを定義することはできません。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40021  
  
### このエラーを解決するには  
  
-   基底クラスのメンバーの追加バージョンを定義しようとしていて、基底クラスのソース コードにアクセスできる場合は、[Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) キーワードを基底クラスの定義に追加します。  
  
-   基底クラスのソース コードへのアクセス権がない場合は、派生クラスのメンバーをオーバーロードすることはできません。`Overloads` キーワードを削除します。  
  
-   基底クラスのメンバーの追加バージョンを定義するのではなく、そのメンバーを置換するには、`Overloads` ではなく、[Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides) キーワードを使用します。  
  
-   派生クラスの新しいメンバーで基底クラスのメンバーを隠ぺいする場合は、`Overloads` ではなく、[Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) キーワードを使用します。  
  
## 参照  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)