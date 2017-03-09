---
title: "初期化するフィールドまたはプロパティの名前は、&#39;.&#39; で始めなければなりません | Microsoft Docs"
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
  - "vbc30985"
  - "bc30985"
helpviewer_keywords: 
  - "BC30985"
ms.assetid: 4cb543e1-477c-429c-82df-541ebff08543
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 初期化するフィールドまたはプロパティの名前は、&#39;.&#39; で始めなければなりません
オブジェクト初期化子リスト内の各メンバー初期化子には、フィールドまたはプロパティの名前とその初期値を指定します。 フィールドまたはプロパティの名前の前にピリオドを付ける必要があります。 たとえば、次の宣言では、`client` の `Name` プロパティの初期値として "Microsoft" を割り当てています。  
  
```  
Dim client As New Customer() With { .Name = "Microsoft" }  
```  
  
 **エラー ID:** BC30985  
  
### このエラーを解決するには  
  
-   各メンバー名にプレフィックスとしてピリオドを付けます。  
  
## 参照  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [ビルド内にありません: プロパティ プロシージャとフィールド](http://msdn.microsoft.com/ja-jp/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)