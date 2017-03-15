---
title: "コンパイラ エラー CS0118 | Microsoft Docs"
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
  - "CS0118"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0118"
ms.assetid: 9a612432-6e56-4e9b-9d8c-7d7b43f58c1a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0118
'construct1\_name' は 'construct1' ですが、'construct2' のように使用されています  
  
 コンパイラにより、構造体が正しくない方法で使用されたか、または許可されていない操作が構成体で試行された状況が検出されました。 いくつかの一般的な例を次に示します。  
  
-   \(クラスではなく\) 名前空間をインスタンス化しようとした  
  
-   \(メソッドではなく\) フィールドを呼び出そうとした  
  
-   型を変数として使用しようとした  
  
-   extern エイリアスを型として使用しようとした  
  
 このエラーを解決するには、実行中の操作が、操作の実行対象である型にとって有効であることを確認します。  
  
## 使用例  
 次の例では CS0118 が生成されます。  
  
```  
// CS0118.cs // compile with: /target:library namespace MyNamespace { class MyClass { // MyNamespace not a class MyNamespace ix = new MyNamespace ();   // CS0118 } }  
```