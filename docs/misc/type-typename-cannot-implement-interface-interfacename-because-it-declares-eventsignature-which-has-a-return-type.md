---
title: "戻り値の型が指定された &#39;&lt;eventsignature&gt;&#39; を宣言しているため、型 &#39;&lt;typename&gt;&#39; は、インターフェイス &#39;&lt;interfacename&gt;&#39; を実装できません | Microsoft Docs"
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
  - "bc30945"
  - "vbc30945"
helpviewer_keywords: 
  - "BC30945"
ms.assetid: 4f26e71a-949d-4103-b565-35cc8e833d29
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 戻り値の型が指定された &#39;&lt;eventsignature&gt;&#39; を宣言しているため、型 &#39;&lt;typename&gt;&#39; は、インターフェイス &#39;&lt;interfacename&gt;&#39; を実装できません
クラスまたは構造体がインターフェイスを実装しようとしていますが、そのインターフェイスには値を返すイベントが宣言されています。  
  
 Visual Basic では、現在、値を返すイベントの宣言をサポートしていません。  
  
 **エラー ID:** BC30945  
  
### このエラーを解決するには  
  
-   `Implements` ステートメントをクラスまたは構造体の定義から削除するか、別のインターフェイスを実装します。  
  
## 参照  
 [NOT IN BUILD: イベントとイベント ハンドラ](http://msdn.microsoft.com/ja-jp/95074a0d-1cbc-4221-a95a-964185c7f962)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NOT IN BUILD: Implements キーワードおよび Implements ステートメント](http://msdn.microsoft.com/ja-jp/b96560f7-6413-480f-a1e2-f80253bab5be)