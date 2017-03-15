---
title: "コンパイラ エラー CS0012 | Microsoft Docs"
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
  - "CS0012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0012"
ms.assetid: 5523e349-22f4-4b0b-b4b0-c4bf26c461f4
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0012
型 'type' は、参照されていないアセンブリに定義されています。 アセンブリ 'assembly' に参照を追加する必要があります。  
  
 参照される型の定義が見つかりませんでした。 このエラーは、必要な .DLL ファイルがコンパイル時にインクルードされていない場合に発生することがあります。 詳細については、次のトピックを参照してください。[Add Reference Dialog Box](http://msdn.microsoft.com/ja-jp/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) および[\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).  
  
 次のコンパイル シーケンスは CS0012 になります。  
  
```  
// cs0012a.cs // compile with: /target:library public class A {}  
```  
  
 次のコードも同様の結果になります。  
  
```  
// cs0012b.cs // compile with: /target:library /reference:cs0012a.dll public class B { public static A f() { return new A(); } }  
```  
  
 次のコードも同様の結果になります。  
  
```  
// cs0012c.cs // compile with: /reference:cs0012b.dll class C { public static void Main() { object o = B.f();   // CS0012 } }  
```  
  
 この CS0012 は、`/reference:cs0012b.dll;cs0012a.dll` を使用してコンパイルするか、Visual Studio で [Add Reference Dialog Box](http://msdn.microsoft.com/ja-jp/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) を使用して cs0012b.dll と cs0012a.dll への参照を追加することで解決できる場合があります。