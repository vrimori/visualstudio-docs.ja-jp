---
title: "コンパイラの警告 (レベル 2) CS1927 | Microsoft Docs"
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
  - "CS1927"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1927"
ms.assetid: 32b4e58f-668c-4596-9529-7f3a293ff4ac
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS1927
モジュールの \/win32manifest は、アセンブリにのみ適用されるため、無視されます。  
  
 Win32 マニフェストはアセンブリ レベルでのみ適用されます。 モジュールはコンパイルされますが、マニフェストはありません。  
  
### このエラーを解決するには  
  
1.  **\/win32manifest option** を削除します。  
  
2.  コードをアセンブリとしてコンパイルします。  
  
## 使用例  
 次の例では、**\/target:module** と **\/win32manifest** の両方のコンパイラ オプションでコンパイルされたときに CS1927 が生成されます。  
  
```  
// cs1927.cs // Compile with: /target:module /win32manifest using System; class ManifestWithModule { static int Main() { return 1; } }  
```  
  
## 参照  
 [\/win32manifest \(Import a Custom Win32 Manifest File\)](/dotnet/csharp/language-reference/compiler-options/win32manifest-compiler-option)   
 [\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md)