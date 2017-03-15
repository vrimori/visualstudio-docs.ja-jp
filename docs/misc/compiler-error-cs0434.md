---
title: "コンパイラ エラー CS0434 | Microsoft Docs"
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
  - "CS0434"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0434"
ms.assetid: 8f8871fc-a4bb-4a9e-ba19-999f4943001e
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0434
NamespaceName2 内の名前空間 NamespaceName1 は、NamespaceName3 内の TypeName1 型と競合します  
  
 このエラーは、インポートされた型とインポート済みの入れ子になった名前空間が同じ完全修飾名を持つ場合に発生します。 その名前が参照されると、コンパイラは 2 つを区別することができません。 インポートしたソース コードを変更できる場合は、型または名前空間のいずれかの名前を変更し、両方がアセンブリ内で一意になるようにすることで、エラーを解決できます。  
  
 次のコードではエラー CS0434 が生成されます。  
  
## 使用例  
 このコードは、同じ完全修飾名を持つ型の最初のコピーを作成します。  
  
```  
// CS0434_1.cs // compile with: /t:library namespace TypeBindConflicts { namespace NsImpAggPubImp { public class X { } } }  
```  
  
## 使用例  
 このコードは、同じ完全修飾名を持つ型の 2 番目のコピーを作成します。  
  
```  
// CS0434_2.cs // compile with: /t:library namespace TypeBindConflicts { // Conflicts with another import (import2.cs). public class NsImpAggPubImp { } // Try this instead: // public class UniqueClassName { } }  
```  
  
## 使用例  
 このコードは、同じ完全修飾名を持つ型を参照します。  
  
```  
// CS0434.cs // compile with: /r:cs0434_1.dll /r:cs0434_2.dll using TypeBindConflicts; public class Test { public TypeBindConflicts.NsImpAggPubImp.X n2 = null; // CS0434 }  
```