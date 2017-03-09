---
title: "コンパイラ エラー CS0011 | Microsoft Docs"
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
  - "CS0011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0011"
ms.assetid: 892553d7-a516-4631-84cd-94db5722c90d
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0011
型 'type' で参照されているアセンブリ 'assembly' の基底クラスまたはインターフェイス 'class' が解決できません  
  
 **\/reference** を使用してファイルからインポートされたクラスが、あるクラスの派生クラスであるか、または見つからないインターフェイスを実装しています。 このエラーは、必要な DLL が **\/reference** を使用したコンパイル時にインクルードされていない場合に発生することがあります。  
  
 詳細については、次のトピックを参照してください。[Add Reference Dialog Box](http://msdn.microsoft.com/ja-jp/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) および[\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).  
  
## 使用例  
  
```  
// CS0011_1.cs // compile with: /target:library public class Outer { public class B { } }  
```  
  
## 使用例  
 2 つ目のファイルでは、前の例で作成した `B` クラスから派生した `C` クラスを定義する DLL を作成します。  
  
```  
// CS0011_2.cs // compile with: /target:library /reference:CS0011_1.dll // post-build command: del /f CS0011_1.dll public class C : Outer.B {}  
```  
  
## 使用例  
 3 つ目のファイルでは、最初の手順で作成した DLL を置き換え、内部クラスである `B` の定義を省略しています。  
  
```  
// CS0011_3.cs // compile with: /target:library /out:cs0011_1.dll public class Outer {}  
```  
  
## 使用例  
 最後に、4 つ目のファイルで、2 番目の例で定義した `C` クラスを参照します。これは `B` クラスから派生していますが、今回、これはありません。  
  
 次の例では CS0011 が生成されます。  
  
```  
// CS0011_4.cs // compile with: /reference:CS0011_1.dll /reference:CS0011_2.dll // CS0011 expected class M { public static void Main() { C c = new C(); } }  
```  
  
## 参照  
 [Add Reference Dialog Box](http://msdn.microsoft.com/ja-jp/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)   
 [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option)