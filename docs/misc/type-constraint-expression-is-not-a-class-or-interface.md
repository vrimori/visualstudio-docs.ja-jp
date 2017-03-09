---
title: "型制約 &#39;&lt;expression&gt;&#39; は、クラスまたはインターフェイスではありません | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32048"
  - "vbc32048"
helpviewer_keywords: 
  - "BC32048"
ms.assetid: 68811886-44ac-43e1-9315-b39857310033
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型制約 &#39;&lt;expression&gt;&#39; は、クラスまたはインターフェイスではありません
制約リストに、型パラメーターについて有効な制約を表していない式が含まれています。  
  
 制約リストでは、型パラメーターに渡される型引数の要件が適用されます。 次の要件を任意の組み合わせで指定できます。  
  
-   型引数はインターフェイスを実装する必要があります  
  
-   型引数は、最大で 1 つのクラスから継承する必要があります  
  
-   型引数では、作成元のコードがアクセスできるパラメーターなしのコンストラクターを公開する必要があります  
  
-   型引数は、参照型または値型である必要があります  
  
 **エラー ID:** BC32048  
  
### このエラーを解決するには  
  
-   式とその要素のスペルが正しいことを確認します。  
  
-   式が上記の要件リストを満たしていない場合は、制約リストから削除します。  
  
-   式でインターフェイスまたはクラスを参照する場合、コンパイラにそのインターフェイスまたはクラスへのアクセス権があることを確認します。 その名前を修飾し、プロジェクトに参照を追加することが必要な場合があります。 詳細については、[「ビルド内にありません: 同じ名前を持つ複数の変数がある場合に参照を解決する」](http://msdn.microsoft.com/ja-jp/9601e39f-1911-44e1-ace5-3f6e090408b9)の「プロジェクトへの参照」を参照してください。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [ビルド内にありません: 方法: 宣言された要素名を修飾する](http://msdn.microsoft.com/ja-jp/6bd112f5-df6f-42b8-9427-a9225bfcbaab)   
 [How to: Add and Remove Project References](http://msdn.microsoft.com/ja-jp/f51b784d-0bc8-4c19-a898-e560d5ed696b)