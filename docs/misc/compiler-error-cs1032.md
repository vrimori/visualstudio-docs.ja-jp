---
title: "コンパイラ エラー CS1032 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1032"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1032"
ms.assetid: fe318a6c-4403-4b9b-b3d8-753ec31c00ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1032
ファイルの最初のトークンの後でプリプロセッサのシンボルの定義または定義の解除を行えませんでした。  
  
 `#define` および `#undef` [プリプロセッサ ディレクティブ](/dotnet/csharp/language-reference/preprocessor-directives/index) は、名前空間宣言で使用されるキーワードなど、他のすべてのキーワードよりも前に、プログラムの先頭で使用する必要があります。  
  
 次の例では CS1032 が生成されます。  
  
```  
// CS1032.cs namespace x { public class clx { #define a   // CS1032, put before namespace public static void Main() { } } }  
```