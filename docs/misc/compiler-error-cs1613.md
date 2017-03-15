---
title: "コンパイラ エラー CS1613 | Microsoft Docs"
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
  - "CS1613"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1613"
ms.assetid: 9d7ea9c8-9953-459f-a3f0-c7e65d1b9f59
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1613
インターフェイス 'interface' のマネージ コクラス ラッパー クラス 'class' が見つかりません \(アセンブリ参照が存在することを確認してください\)  
  
 インターフェイスから COM オブジェクトをインスタンス化しようとしました。 インターフェイスに **ComImport** 属性と `CoClass` 属性がありますが、`CoClass` 属性に指定された型をコンパイラが見つけられません。  
  
 このエラーを解決するには、次のいずれかを試すことができます。  
  
-   コクラスを含むアセンブリへの参照を追加します \(ほとんどの場合、インターフェイスとコクラスは同じアセンブリにあります\)。 詳細については、「[\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option)」または「[&#91;参照の追加&#93; ダイアログ ボックス](http://msdn.microsoft.com/ja-jp/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)」を参照してください。  
  
-   インターフェイスの `CoClass` 属性を修正します。  
  
 次の例では、**CoClassAttribute** の正しい使用法を示しています。  
  
```  
// CS1613.cs using System; using System.Runtime.InteropServices; [Guid("1FFD7840-E82D-4268-875C-80A160C23296")] [ComImport()] [CoClass(typeof(A))] public interface IA{} public class A : IA {} public class AA { public static void Main() { IA i; i = new IA(); // This is equivalent to new A(). // because of the CoClass attribute on IA } }  
```