---
title: "コンパイラ エラー CS2036 | Microsoft Docs"
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
  - "CS2036"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2036"
ms.assetid: 44b73be4-b792-4735-bdbd-bd757ab22683
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS2036
\/pdb オプションでは、\/debug オプションも使用する必要があります。  
  
 プログラム データベース ファイルは、デバッグ ビルドについてのみ生成されます。 そのため、**\/pdb** オプションは、製品版ビルドでは意味がありません。  
  
### このエラーを解決するには  
  
-   **\/debug** コンパイラ オプションを追加します。  
  
-   **\/pdb** コンパイラ オプションを削除します。  
  
## 使用例  
 **\/pdb** オプションを使用して \/debug オプションは使用せずにコンパイルする次の例では、CS2036 が生成されます。  
  
```  
// cs2036.cs // Compile with: /pdb // CS2036 class Test { public static int Main() { return 1; } }  
```  
  
## 参照  
 [\/pdb \(Specify Debug Symbol File\)](/dotnet/csharp/language-reference/compiler-options/pdb-compiler-option)   
 [\/debug \(Emit Debugging Information\)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)