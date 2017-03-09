---
title: "この &#39;Sub New&#39; の最初のステートメントは、&#39;MyBase.New&#39; または &#39;MyClass.New&#39; への呼び出しでなければなりません (パラメーターのないアクセス可能なコンストラクターが複数あります)。 | Microsoft Docs"
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
  - "vbc32038"
  - "bc32038"
helpviewer_keywords: 
  - "BC32038"
ms.assetid: 52e4e9df-a85b-46ae-a0cc-7d8fa377fe95
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# この &#39;Sub New&#39; の最初のステートメントは、&#39;MyBase.New&#39; または &#39;MyClass.New&#39; への呼び出しでなければなりません (パラメーターのないアクセス可能なコンストラクターが複数あります)。
'\<derived\>' の基底クラス '\<base\>' には、引数なしで呼び出せるアクセス可能な 'Sub New' が 2 つ以上指定されているため、この 'Sub New' の最初のステートメントは、'MyBase.New' または 'MyClass.New' への呼び出しでなければなりません。  
  
 クラス コンストラクターで、基底クラス コンストラクターの呼び出しが指定されていません。また、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では暗黙の呼び出しを指定できません。これは、呼び出しの対象となる基底クラス コンストラクターを判断できないためです。  
  
 **エラー ID:** BC32038  
  
### このエラーを解決するには  
  
-   このコンストラクターの最初の行として、基底クラス コンストラクター `MyBase.New()` の呼び出しを追加するか、`MyClass.New()` または `Me.New()` を使用して、このクラスにある別のコンストラクターの呼び出しを追加します。  
  
## 参照  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NOT IN BUILD: コンストラクターとデストラクターの使用方法](http://msdn.microsoft.com/ja-jp/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [MyBase \- 削除](http://msdn.microsoft.com/ja-jp/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)