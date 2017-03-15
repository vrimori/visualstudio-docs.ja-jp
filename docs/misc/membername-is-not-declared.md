---
title: "&#39;&lt;membername&gt;&#39; が宣言されていません | Microsoft Docs"
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
  - "vbc30816"
  - "bc30816"
helpviewer_keywords: 
  - "BC30816"
ms.assetid: d6704bed-bb76-47c6-ac28-09608d5e6912
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;membername&gt;&#39; が宣言されていません
'`<membername>`' が宣言されていません。`Debug` オブジェクト機能は、`System` アセンブリの `System.Diagnostics.Debug` で使用できます。  
  
 指定したメンバー名が見つかりませんでした  
  
 **エラー ID:** BC30816  
  
### このエラーを解決するには  
  
1.  メンバーのスペルを確認します。  
  
2.  `Imports` ステートメントを使用するか、または他の名前空間に定義されたメンバーを完全に修飾します。 たとえば、`WriteLine` 関数は `System.Diagnostics.Debug` 名前空間に宣言されています。  
  
## 参照  
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)