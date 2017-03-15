---
title: "&#39;=&#39; が必要です (オブジェクト初期化子) | Microsoft Docs"
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
  - "vbc30984"
  - "bc30984"
helpviewer_keywords: 
  - "BC30984"
ms.assetid: 9cae8d32-775a-414f-9e51-0469974b6aab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;=&#39; が必要です (オブジェクト初期化子)
オブジェクト初期化子の宣言でフィールドまたはプロパティの初期値を確立するには、等号を使用する必要があります。 たとえば、次の宣言では、`client` の `Name` プロパティの初期値として "Microsoft" を割り当てています。  
  
```  
Dim client As New Customer { .Name = "Microsoft" }  
```  
  
 **エラー ID:** BC30984  
  
### このエラーを解決するには  
  
-   前の例で示した位置に等号を追加します。  
  
## 参照  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [ビルド内にありません: プロパティとプロパティ プロシージャ](http://msdn.microsoft.com/ja-jp/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [ビルド内にありません: プロパティ プロシージャとフィールド](http://msdn.microsoft.com/ja-jp/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)