---
title: "引数 &#39;Life&#39; を 0 にすることはできません | Microsoft Docs"
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
  - "vbrFinancial_LifeNEZero"
ms.assetid: c402da97-a2b2-4219-a83a-0cebbfdffef2
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 引数 &#39;Life&#39; を 0 にすることはできません
`Life` の引数が正しくありません。これは、資産の耐用年数を指定する `Double` である必要があります。  
  
### このエラーを解決するには  
  
-   式の引数のスペルを確認します。 変数名のスペルが間違っていると、0 に初期化される数値型の変数が暗黙的に生成されることがあります。  
  
-   式の変数 \(特に、他のプロシージャから引数としてプロシージャに渡されたもの\) に対してこれまで実行した操作を確認します。  
  
## 参照  
 [ビルド内にありません: DDB 関数](http://msdn.microsoft.com/ja-jp/c7cf8929-d158-4399-b3cb-31d897d12556)   
 [ビルド内にありません: SYD 関数](http://msdn.microsoft.com/ja-jp/23c25672-f5dd-49ac-9893-4faa82634181)   
 [ビルド内にありません: SLN 関数](http://msdn.microsoft.com/ja-jp/8e06130a-056e-4266-a8a9-1592b86f58d2)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)