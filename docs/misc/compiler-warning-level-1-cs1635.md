---
title: "コンパイラの警告 (レベル 1) CS1635 | Microsoft Docs"
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
  - "CS1635"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1635"
ms.assetid: e1795880-f7ea-4dca-b15b-4ba549d7ed78
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS1635
警告 'warning code' はグローバルで無効にされたため、復元することはできません  
  
 この警告は、**\/nowarn** コマンド ライン オプションまたはプロジェクト設定を使用して、コンパイル ユニット全体の警告を無効にしたにもかかわらず、`#pragma warning restore` を使用して警告を復元しようとした場合に発生します。 このエラーを解決するには、\/nowarn のコマンド ライン オプションまたはプロジェクト設定を削除するか、コマンド ラインまたはプロジェクト設定で無効にするすべての警告について、`#pragma warning restore` を削除します。 詳細については、[\#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) のトピックを参照してください。  
  
 次の例では CS1635 が生成されます。  
  
```  
// CS1635.cs // compile with: /w:1 /nowarn:162 enum MyEnum {one=1,two=2,three=3}; class MyClass { public static void Main() { #pragma warning disable 162 if (MyEnum.three == MyEnum.two) System.Console.WriteLine("Duplicate"); #pragma warning restore 162 } }  
```