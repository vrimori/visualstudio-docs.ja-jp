---
title: "クラス &#39;&lt;classname&gt;&#39; にはアクセス可能な &#39;Sub New&#39; が含まれていません。このクラスを継承できません。 | Microsoft Docs"
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
  - "vbc31399"
  - "BC31399"
helpviewer_keywords: 
  - "BC31399"
ms.assetid: 035b333f-ff6a-4fc4-bd36-82f40b1d8bab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# クラス &#39;&lt;classname&gt;&#39; にはアクセス可能な &#39;Sub New&#39; が含まれていません。このクラスを継承できません。
クラスでは、[Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement) を使用して基底クラスを指定していますが、目的の基底クラス上のどのコンストラクターにもアクセスできません。  
  
 このことは、目的の基底クラスにコンストラクターが存在しないか、または基底クラスのコンストラクターに、別のクラスからのアクセスを禁止するアクセス レベルが設定されている場合、発生する可能性があります。  
  
 クラスを継承する場合は、コンストラクターで [MyBase \- delete](http://msdn.microsoft.com/ja-jp/52491d06-6451-4f6f-9aa6-8fab59bbc2b9) を使用して、基底クラス コンストラクターを呼び出す必要があります。 この呼び出しを行わないか、または明示的なコンストラクターの記述も行わない場合は、Visual Basic により、`MyBase.New()` を呼び出す暗黙的なコンストラクターが生成されます。  
  
 **エラー ID:** BC31399  
  
### このエラーを解決するには  
  
1.  目的の基底クラスに対してソース管理が有効な場合は、別のクラスがアクセスできるように、少なくとも 1 つのコンストラクターのアクセス レベルを変更します。  
  
2.  目的の基底クラス コンストラクターのアクセス レベルを変更することができない場合、別のクラスから継承するか、または一切継承しません。  
  
## 参照  
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [MyBase \- delete](http://msdn.microsoft.com/ja-jp/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)