---
title: "&lt;type&gt; パラメーターを &#39;ParamArray&#39; として宣言することはできません | Microsoft Docs"
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
  - "bc33009"
  - "vbc33009"
helpviewer_keywords: 
  - "BC33009"
ms.assetid: faba9aef-ca4e-4c4d-934c-a3e3d3fa3c3e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type&gt; パラメーターを &#39;ParamArray&#39; として宣言することはできません
デリゲート、イベント、または演算子の定義で [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray) パラメーターを宣言しています。  
  
 `ParamArray` パラメータは、`Declare`、`Function`、`Property`、`Sub` のパラメータでのみ使用できます。  
  
 **エラー ID:** BC33009  
  
### このエラーを解決するには  
  
-   パラメーター リストから `ParamArray` キーワードを削除します。  
  
-   演算子を定義している場合は、`ParamArray` の機能を一連のオーバーロードで実現できることがあります。  
  
-   デリゲートまたはイベントを定義する場合は、アプリケーションのこの部分のロジック全体を記述し直す必要があります。 デリゲートまたはイベントのパラメータには、[Optional](/dotnet/visual-basic/language-reference/modifiers/optional) パラメータ、`ParamArray` パラメータ、またはオーバーロードされたパラメータを使用できません。  
  
## 参照  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)