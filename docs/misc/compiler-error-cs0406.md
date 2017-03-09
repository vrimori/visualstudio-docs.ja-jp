---
title: "コンパイラ エラー CS0406 | Microsoft Docs"
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
  - "CS0406"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0406"
ms.assetid: 9d69681c-e261-4e5e-9361-ea566de12f2e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0406
クラス型制約 'constraint' は、他の制約の前に指定する必要があります  
  
 ジェネリック型またはメソッドにクラス型の制約がある場合、その制約がリストの先頭に配置されている必要があります。 このエラーを回避するには、クラス型の制約を制約リストの先頭に移動します。  
  
## 使用例  
 次の例では CS0406 が生成されます。  
  
```  
// CS0406.cs // compile with: /target:library interface I {} class C {} class D<T> where T : I, C {}   // CS0406 class D2<T> where T : C, I {}   // OK  
```