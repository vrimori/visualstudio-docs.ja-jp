---
title: "&#39;New&#39; をインターフェイスで使用することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30375"
  - "bc30375"
helpviewer_keywords: 
  - "BC30375"
ms.assetid: c1e06108-1b52-4cbe-8cae-e816a0dbac0b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; をインターフェイスで使用することはできません
変数がインターフェイス型であることを宣言するときに、[Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement) で [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator) 句が使用されています。  
  
 インターフェイスは参照型ですが、そのインスタンスを作成することはできません。 クラスまたは構造体のインスタンスを作成する場合にのみ、`New` を使用できます。  
  
 **エラー ID:** BC30375  
  
### このエラーを解決するには  
  
1.  変数がインターフェイス型の場合は、`New` キーワードを削除します。  
  
2.  変数がインスタンスを参照する場合は、この変数をクラス型または構造体型として宣言します。 インスタンスを作成するには、`New` キーワードを保持します。  
  
## 参照  
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)