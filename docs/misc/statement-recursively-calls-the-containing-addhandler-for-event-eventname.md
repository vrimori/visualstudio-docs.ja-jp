---
title: "ステートメントはイベント &#39;&lt;eventname&gt;&#39; の包まれている &#39;AddHandler&#39; を再帰的に呼び出しています | Microsoft Docs"
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
  - "bc41998"
  - "vbc41998"
helpviewer_keywords: 
  - "BC41998"
ms.assetid: 4375b191-fbd9-4e93-b9bb-9159d533ddf6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ステートメントはイベント &#39;&lt;eventname&gt;&#39; の包まれている &#39;AddHandler&#39; を再帰的に呼び出しています
イベント定義の `AddHandler` アクセサー内のステートメントは、イベントを直接参照できません。  
  
 イベントが定義されたクラス、構造体、またはモジュールのプライベート フィールドとして、イベントのハンドラーの一覧を格納するという方法をお勧めします。 詳細については、[How to: Declare Custom Events To Avoid Blocking](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md) および [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md) を参照してください。  
  
 **エラー ID:** BC41998  
  
### このエラーを解決するには  
  
-   イベント定義を書き換えて、再帰を回避します。  
  
## 参照  
 [AddHandler \- 削除](http://msdn.microsoft.com/ja-jp/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [How to: Declare Custom Events To Avoid Blocking](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)