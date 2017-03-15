---
title: "コンパイラの警告 (レベル 1) CS0824 | Microsoft Docs"
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
  - "CS0824"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0824"
ms.assetid: ad643bb7-51b2-455b-a9f3-2bd4588d2c5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS0824
コンストラクター 'name' は、external としてマークされています。  
  
 コンストラクターは、extern としてマークされる可能性があります。 ただし、コンパイラは、コンストラクターが実際に存在することを確認することはできません。 そのため、警告が生成されます。  
  
### この警告を削除するには  
  
1.  pragma 警告ディレクティブを使用して、それを無視します。  
  
2.  コンストラクターを型の中に移動します。  
  
## 使用例  
 次のコードでは CS0824 が生成されます。  
  
```  
// cs0824.cs public class C { extern C(); // CS0824 public static int Main() { return 1; } }  
```  
  
## 参照  
 [extern](/dotnet/csharp/language-reference/keywords/extern)   
 [\#pragma 警告](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning)