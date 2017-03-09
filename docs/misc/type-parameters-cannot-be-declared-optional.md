---
title: "&lt;type&gt; パラメーターを &#39;Optional&#39; として宣言することはできません | Microsoft Docs"
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
  - "bc33010"
  - "vbc33010"
helpviewer_keywords: 
  - "BC33010"
ms.assetid: ec4023e7-9ba6-4532-a6b9-4ae6b4f9063a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type&gt; パラメーターを &#39;Optional&#39; として宣言することはできません
デリゲート、イベント、または演算子の定義で [Optional](/dotnet/visual-basic/language-reference/modifiers/optional) パラメーターを宣言しています。  
  
 `Optional` パラメーターは、`Declare`、`Function`、`Property`、`Sub` のパラメーターでのみ使用できます。  
  
 **エラー ID:** BC33010  
  
### このエラーを解決するには  
  
-   パラメーター リストから `Optional` キーワードを削除します。  
  
-   演算子を定義する場合は、`Optional` の機能を一連のオーバーロードで実現できることがあります。  
  
-   デリゲートまたはイベントを定義する場合は、アプリケーションのこの部分のロジック全体を記述し直す必要があります。 デリゲートまたはイベントのパラメーターには、`Optional` パラメーター、[ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray) パラメーター、またはオーバーロードされたバージョンは使用できません。  
  
## 参照  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)