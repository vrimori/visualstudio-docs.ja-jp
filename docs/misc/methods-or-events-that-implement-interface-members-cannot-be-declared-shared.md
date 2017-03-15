---
title: "インターフェイス メンバーを実装するメソッドまたはイベントを、&#39;Shared&#39; として宣言することはできません | Microsoft Docs"
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
  - "bc30505"
  - "vbc30505"
helpviewer_keywords: 
  - "BC30505"
ms.assetid: a24937c5-aeac-47de-a08b-d8696dd8221a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# インターフェイス メンバーを実装するメソッドまたはイベントを、&#39;Shared&#39; として宣言することはできません
インターフェイス メンバーを実装するメソッドまたはイベントを `Shared` として宣言しようとしました。 継承不可能なクラスを除き、クラスに実装されているメソッドやイベントを `Shared` または `Private` と指定することはできません。  
  
 **エラー ID:** BC30505  
  
### このエラーを解決するには  
  
-   `Shared` キーワードを削除します。  
  
## 参照  
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)