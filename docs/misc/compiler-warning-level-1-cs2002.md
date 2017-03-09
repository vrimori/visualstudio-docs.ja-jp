---
title: "コンパイラの警告 (レベル 1) CS2002 | Microsoft Docs"
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
  - "CS2002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2002"
ms.assetid: 4acd054e-d3fe-4be6-a660-53a0a5e8c6a4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS2002
ソース ファイル 'file' が複数回指定されました  
  
 1 つのソース ファイル名が 2 回以上コンパイラに渡されました。 出力ファイルの作成のために、コンパイラには 1 つのファイルを 1 回のみ指定できます。  
  
 この警告は [\/nowarn](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option) オプションで抑制できません。  
  
 次の例では CS2002 が生成されます。  
  
```  
// CS2002.cs // compile with: CS2002.cs public class A { public static void Main(){} }  
```  
  
 このエラーを生成するには、この例をコマンド ラインでコンパイルしてください。  
  
```  
csc CS2002.cs CS2002.cs  
```