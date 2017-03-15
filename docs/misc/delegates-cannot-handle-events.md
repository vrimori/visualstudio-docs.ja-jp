---
title: "デリゲートでイベントを処理することはできません | Microsoft Docs"
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
  - "bc30019"
  - "vbc30019"
helpviewer_keywords: 
  - "BC30019"
ms.assetid: 7f0c7bb9-8e81-44bf-acc5-80d9785708aa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# デリゲートでイベントを処理することはできません
デリゲートは、共有プロシージャまたはオブジェクトのインスタンス プロシージャを指す参照型です。 デリゲートが指すプロシージャは代入によって変更できるため、`Delegate` ステートメントは `Handles` または `Implements` 句をサポートできません。  
  
 **エラー ID:** BC30019  
  
### このエラーを解決するには  
  
-   `Delegate` ステートメントから `Handles` 句を削除します。  
  
## 参照  
 [ビルド内にありません: デリゲートと AddressOf 演算子](http://msdn.microsoft.com/ja-jp/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)