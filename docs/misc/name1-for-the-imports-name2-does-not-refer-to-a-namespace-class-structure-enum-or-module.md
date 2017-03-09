---
title: "インポート &#39;&lt;name2&gt;&#39; の &#39;&lt;name1&gt;&#39; は、Namespace、Class、Structure、Enum、または Module を参照していません | Microsoft Docs"
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
  - "vbc30467"
  - "bc30467"
helpviewer_keywords: 
  - "BC30467"
ms.assetid: a4b8a23b-ba1b-44f7-9584-258dd2607581
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# インポート &#39;&lt;name2&gt;&#39; の &#39;&lt;name1&gt;&#39; は、Namespace、Class、Structure、Enum、または Module を参照していません
`Namespace`、`Class`、`Structure`、`Enum`、または `Module` 以外で `Imports` ステートメントを使用しようとしました。`Imports` ステートメントは参照先のプロジェクトおよびアセンブリから名前空間名をインポートするか、そのステートメントが出現するモジュールと同じプロジェクト内に定義されている名前空間名をインポートします。  
  
 **エラー ID:** BC30467  
  
### このエラーを解決するには  
  
-   インポートしようとしたエンティティを確認して、`Imports` ステートメントで使用できる有効なエンティティであることを確認します。  
  
## 参照  
 [Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [References and the Imports Statement](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)