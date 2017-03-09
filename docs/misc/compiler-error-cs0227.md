---
title: "コンパイラ エラー CS0227 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0227"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0227"
ms.assetid: b595a1c9-8204-4ff7-a1d0-258b0b1d6ff7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0227
アンセーフ コードは \/unsafe でコンパイルした場合のみ有効です。  
  
 ソース コードに [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) キーワードが含まれている場合、[\/unsafe](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option) コンパイラ オプションも使用する必要があります。 詳細については、「[unsafe コードとポインター](/dotnet/csharp/programming-guide/unsafe-code-pointers/index)」を参照してください。  
  
 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] で unsafe オプションを設定するには、メイン メニューで **\[プロジェクト\]** をクリックして、**\[ビルド\]** ウィンドウを選択し、\[アンセーフ コードの許可\] チェック ボックスをオンにします。  
  
 次の例で、**\/unsafe** なしでコンパイルすると、CS0227 が生成されます。  
  
```  
// CS0227.cs public class MyClass { unsafe public static void Main()   // CS0227 { } }  
```  
  
## 参照  
 [C\# Compiler Errors](/dotnet/csharp/language-reference/compiler-messages/index)