---
title: "コンパイラ エラー CS0828 | Microsoft Docs"
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
  - "CS0828"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0828"
ms.assetid: e18ffe72-2fcc-436d-be7f-8c8365b86129
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0828
'expression' を、匿名型プロパティに割り当てることはできません。  
  
 匿名型は、null 値、安全ではない型、メソッド グループ、および匿名関数で初期化できません。  
  
### このエラーを解決するには  
  
1.  型宣言を割り当ての左側に追加するか、適切な型が指定されるように右側の式を変更します。  
  
## 使用例  
 次のコードは、匿名型のメンバーを null 値で初期化できないため、CS0828 を生成します。  
  
```  
// cs0828.cs using System; public class C { public static int Main() { var a = 1; var c = new { p1 = null }; // CS0828 return 1; } }  
```  
  
## 参照  
 [暗黙的に型指定されるローカル変数](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)