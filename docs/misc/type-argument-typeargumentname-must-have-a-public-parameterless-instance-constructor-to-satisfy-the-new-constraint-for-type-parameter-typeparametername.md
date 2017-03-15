---
title: "型パラメーター &#39;&lt;typeparametername&gt;&#39; の &#39;New&#39; 制約を満たすには、型引数 &#39;&#39;&lt;typeargumentname&gt;&#39;&#39; にパブリックのパラメーターなしインターフェイス コンストラクターを指定しなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32083"
  - "BC32083"
helpviewer_keywords: 
  - "BC32083"
ms.assetid: 56bf25f1-375c-4b5d-9969-45eba8b3b66c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーター &#39;&lt;typeparametername&gt;&#39; の &#39;New&#39; 制約を満たすには、型引数 &#39;&#39;&lt;typeargumentname&gt;&#39;&#39; にパブリックのパラメーターなしインターフェイス コンストラクターを指定しなければなりません
型引数は [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator) 制約が指定された型パラメーターに対して、アクセス可能なパラメーターなしコンストラクターがない型を指定しています。  
  
 制約リストでは、型パラメーターに渡される型引数の要件が適用されます。 適用可能な要件の 1 つは、作成元のコードがアクセスできるパラメーターなしのコンストラクターを、型引数が公開する必要があることです。 この要件を指定するには、制約リストに `New` 制約を定義します。  
  
 **エラー ID:** BC32083  
  
### このエラーを解決するには  
  
1.  ジェネリック型の名前と、型引数の型名のスペルが正しいことを確認します。  
  
2.  アクセス可能なパラメーターなしのコンストラクターを公開する型引数の型を選択します。 このような型引数を、この型パラメーターに指定できる場合を除き、この特定のジェネリック型を呼び出すことはできません。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [方法 : ジェネリック クラスを使用する](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)