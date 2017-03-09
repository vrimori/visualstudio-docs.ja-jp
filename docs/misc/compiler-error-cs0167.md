---
title: "コンパイラ エラー CS0167 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0167"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0167"
ms.assetid: e6901b40-11a0-422c-9ea3-3b25c0ad7791
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0167
デリゲート 'delegate' に Invoke メソッドがありません。  
  
 別のコンパイラで作成したマネージ プログラム \(.NET Framework 共通言語ランタイムを使用するプログラム\) をインポートして使用しました。 そのコンパイラでは、正しくない形式の[デリゲート](/dotnet/csharp/language-reference/keywords/delegate)が許可されています。 このため、`Invoke` メソッドを使用できませんでした。 詳細については、「[デリゲート](/dotnet/csharp/programming-guide/delegates/index)」を参照してください。