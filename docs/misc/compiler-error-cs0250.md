---
title: "コンパイラ エラー CS0250 | Microsoft Docs"
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
  - "CS0250"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0250"
ms.assetid: a994f361-6287-4db0-9ce1-e293a8190049
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0250
基底クラスの Finalize メソッドを直接呼び出さないでください。 デストラクターから自動的に呼び出されます。  
  
 プログラムでは基底クラスのリソースを強制的にクリーンアップできません。  
  
 詳細については、「[Finalize メソッドおよびデストラクター](http://msdn.microsoft.com/ja-jp/fd376774-1643-499b-869e-9546a3aeea70)」を参照してください。  
  
 次の例では CS0250 が生成されます  
  
```  
// CS0250.cs class B { } class C : B { ~C() { base.Finalize();   // CS0250 } public static void Main() { } }  
```