---
title: "&#39;TypeOf...Is&#39; の左には参照型を持つオペランドが必要ですが、このオペランドの型は &#39;&lt;type&gt;&#39; です | Microsoft Docs"
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
  - "bc30021"
  - "vbc30021"
helpviewer_keywords: 
  - "BC30021"
ms.assetid: a6e76fc8-9c7f-4e55-8b68-e6e7b03a6737
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;TypeOf...Is&#39; の左には参照型を持つオペランドが必要ですが、このオペランドの型は &#39;&lt;type&gt;&#39; です
`TypeOf...Is` 式は、オブジェクト変数の実行時の型の互換性をチェックします。 この互換性は、値型に対して定義されていません。  
  
 **エラー ID:** BC30021  
  
### このエラーを解決するには  
  
-   `Option Strict` が `Off` の場合は、`TypeName` または `VarType` の関数を使用して変数のデータ型の情報を取得します。  
  
-   `Option Strict` が `On` の場合は、変数宣言で変数のデータ型を決定します。  
  
## 参照  
 [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [ビルド内にありません: TypeName 関数 \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/6197bc6c-e8a6-4711-883c-0c95e94e272c)   
 [ビルド内にありません: VarType 関数 \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/e820b6fc-faa6-4de4-836a-0466032dc190)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)