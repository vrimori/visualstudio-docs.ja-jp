---
title: "&#39;&lt;eventname&gt;&#39; は &#39;&lt;containername&gt;&#39; のイベントではありません | Microsoft Docs"
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
  - "vbc30676"
  - "bc30676"
helpviewer_keywords: 
  - "BC30676"
ms.assetid: 16875ec2-94bd-45fd-9198-cc72772d4878
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;eventname&gt;&#39; は &#39;&lt;containername&gt;&#39; のイベントではありません
指定されたイベントは、オブジェクトに対して宣言されていません。  
  
 **エラー ID:** BC30676  
  
### このエラーを解決するには  
  
1.  イベント名のスペルを確認します。  
  
2.  正しいオブジェクトにアクセスしていることを確認します。 オブジェクトへの完全修飾参照を使用するか、`Imports` ステートメントを使用して必要に応じて適切な名前空間をインポートします。  
  
## 参照  
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)   
 [Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)