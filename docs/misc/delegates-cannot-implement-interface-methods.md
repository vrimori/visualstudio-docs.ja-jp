---
title: "デリゲートでインターフェイス メソッドを実装することはできません | Microsoft Docs"
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
  - "bc30018"
  - "vbc30018"
helpviewer_keywords: 
  - "BC30018"
ms.assetid: 71851072-c0c7-4131-aaf7-f3e9e6a2a448
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# デリゲートでインターフェイス メソッドを実装することはできません
デリゲートは、共有プロシージャまたはオブジェクトのインスタンス プロシージャを指す参照型です。 デリゲートが指すプロシージャは代入によって変更できるため、`Delegate` ステートメントは `Handles` または `Implements` 句をサポートできません。  
  
 **エラー ID:** BC30018  
  
### このエラーを解決するには  
  
-   `Delegate` ステートメントから `Implements` 句を削除します。  
  
## 参照  
 [ビルド内にありません: デリゲートと AddressOf 演算子](http://msdn.microsoft.com/ja-jp/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)