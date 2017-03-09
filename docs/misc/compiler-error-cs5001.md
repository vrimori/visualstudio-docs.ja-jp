---
title: "コンパイラ エラー CS5001 | Microsoft Docs"
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
  - "CS5001"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS5001"
ms.assetid: e1e26e75-84e0-47c7-be8a-3c4fd0d6f497
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS5001
プログラム 'program' は、エントリ ポイントに適切な静的 'Main' メソッドを含んでいません  
  
 このエラーは、実行可能ファイルとして生成されるコードに、正しく署名された静的 [Main](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments) メソッドが見つからない場合に発生します。 このエラーは、エントリ ポイント関数が大文字と小文字を間違えて定義されている場合 \(たとえば、`Main` を小文字で `main` と表記するなど\) にも発生します。  
  
-   `Main` は静的として宣言され、[void](/dotnet/csharp/language-reference/keywords/void) または [int](/dotnet/csharp/language-reference/keywords/int) を返す必要があります。また、パラメーターを持たないか、型 `string[]` のパラメーターを 1 つ持つ必要があります。  
  
## 使用例  
 次の例では、CS5001 エラーが生成されます。  
  
```  
// CS5001.cs // CS5001 expected public class a { // Uncomment the following line to resolve. // static void Main() {} }  
```  
  
## 参照  
 [Main\(\) とコマンド ライン引数](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments)