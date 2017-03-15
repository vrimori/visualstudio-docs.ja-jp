---
title: "コンパイラ エラー CS1725 | Microsoft Docs"
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
  - "cs1725"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1725"
ms.assetid: baef9ae3-b036-41d6-972c-9f3cdae1e8bd
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1725
フレンド アセンブリ参照 'reference' は使用できません。 InternalsVisibleTo 宣言に、バージョン、カルチャ、公開キー トークン、またはプロセッサ アーキテクチャを指定することはできません。  
  
 フレンド アセンブリの参照では、バージョン カルチャを追加できません。 部分クラスは、フレンド アセンブリから参照できる必要があります。  
  
## 使用例  
 次の例では CS1725 が生成されます。  
  
```  
// CS1725.cs // compile with: /target:library using System.Runtime.CompilerServices; [assembly:InternalsVisibleTo("partial01,version=1.1.0.0")]   // CS1725 // try the following line instead // [assembly:InternalsVisibleTo("partial01")] partial class TestClass { public static string strBar = "my string"; }  
```  
  
## 参照  
 [方法: 署名されたフレンド アセンブリを作成する](../Topic/How%20to:%20Create%20Signed%20Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)