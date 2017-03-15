---
title: "ステートメントは、イベント本体内部には記述できません | Microsoft Docs"
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
  - "bc31112"
  - "vbc31112"
helpviewer_keywords: 
  - "BC31112"
ms.assetid: fd51fc53-a008-4b79-85fb-2d9fa1fb5a79
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ステートメントは、イベント本体内部には記述できません
ステートメントは、イベント本体内部には記述できません。 イベントの終了が想定されます。  
  
 イベント本体内部では有効ではないステートメントが、内部に出現します。  
  
 **エラー ID:** BC31112  
  
### このエラーを解決するには  
  
-   ステートメントの前に `End Event` を追加します。  
  
## 参照  
 [Application Events Sample](http://msdn.microsoft.com/ja-jp/289a787f-b97e-43c8-a304-fe95e45f4a0d)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)