---
title: "コンパイラ エラー CS0454 | Microsoft Docs"
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
  - "CS0454"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0454"
ms.assetid: 2c83bc5e-53bb-473e-92aa-5122dadd79d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0454
'Type Parameter 1' と 'Type Parameter 2' を含む循環制約の依存関係  
  
 このエラーは、ある時点で 1 つの型パラメーターが別の型パラメーターを参照し、2 つ目の型パラメーターが最初の型パラメーターを逆参照します。 このエラーを解決するには、制約のいずれかを削除して、循環依存の関係をなくします。 循環制約の依存関係は間接である場合があることに注意してください。  
  
## 使用例  
 次のコードではエラー CS0454 が生成されます。  
  
```  
// CS0554 using System; public class GenericsErrors { public class G4<T> where T : T { } // CS0454 }  
```  
  
## 使用例  
 次の例は、2 つの型制約の間にある循環依存の関係を示します。  
  
```  
public class Gen<T,U> where T : U where U : T  // CS0454 { }  
```