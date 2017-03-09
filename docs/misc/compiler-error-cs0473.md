---
title: "コンパイラ エラー CS0473 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0473"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0473"
ms.assetid: 58eb141e-7da0-41c8-b868-7cd2a15f07f9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0473
明示的なインターフェイスの実装 'method name' に一致するインターフェイス メンバーが 2 つ以上あります。 実際にどのインターフェイス メンバーが選択されるかは実装に依存しています。 代わりに、明示的ではない実装の使用をお勧めします。  
  
 ジェネリック メソッドが非ジェネリック メソッドと同じシグネチャを取得する場合があります。 問題は、どのメソッドがどのスロットにバインドするか明確に示すための方法が、共通言語基盤 \(CLI: Common Language Infrastructure\) のメタデータ システムにないことです。 この決定は CLI により行われます。  
  
> [!NOTE]
>  Visual Studio 2008 の場合、このエラーは、Visual Studio 2005 では起こらなかった位置で発生します。  
  
### このエラーを解決するには  
  
1.  明示的な実装を除去し、暗黙的な実装 `public int TestMethod(int)` だけで両方のインターフェイス メソッドを実装します。  
  
## 使用例  
 次のコードでは CS0473 が生成されます。  
  
```  
// cs0473.cs public interface ITest<T> { int TestMethod(int i); int TestMethod(T i); } public class ImplementingClass : ITest<int> { int ITest<int>.TestMethod(int i) // CS0473 { return i + 1; } public int TestMethod(int i) { return i - 1; } } class T { static int Main() { ImplementingClass a = new ImplementingClass(); if (a.TestMethod(0) != -1) return -1; ITest<int> i_a = a; System.Console.WriteLine(i_a.TestMethod(0).ToString()); if (i_a.TestMethod(0) != 1) return -1; return 0; } }  
  
```  
  
## 参照  
 [Fabulous Adventures in Coding \(コーディングのすてきな冒険\)](http://blogs.msdn.com/ericlippert/archive/2006/04/06/570126.aspx)