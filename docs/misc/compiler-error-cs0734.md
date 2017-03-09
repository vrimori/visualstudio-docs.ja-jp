---
title: "コンパイラ エラー CS0734 | Microsoft Docs"
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
  - "CS0734"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0734"
ms.assetid: 9e1b0e49-bfc3-400c-9fd1-37e3c827e656
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0734
\/moduleassemblyname オプションは 'module' のターゲット型をビルドするときのみ指定できます。  
  
 コンパイラ オプション **\/moduleassemblyname** は、.netmodule をビルドするときのみ使用する必要があります。 詳細については、「[\/moduleassemblyname \(Specify Friend Assembly for Module\)](/dotnet/csharp/language-reference/compiler-options/moduleassemblyname-compiler-option)」を参照してください。  
  
 .netmodule をビルドする方法の詳細については、「[\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md)」を参照してください。  
  
## 使用例  
 次の例では CS0734 が生成されます。 解決するには、**\/target:module** をコンパイルに追加します。  
  
```  
// CS0734.cs // compile with: /moduleassemblyname:A // CS0734 expected public class Test {}  
```