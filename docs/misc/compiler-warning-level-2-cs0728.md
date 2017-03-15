---
title: "コンパイラの警告 (レベル 2) CS0728 | Microsoft Docs"
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
  - "CS0728"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0728"
ms.assetid: ad6d860d-bac4-48f3-9eab-1efd2b6de6c0
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS0728
using または lock ステートメントの引数であるローカルの 'variable' への割り当てが間違っている可能性があります。  Dispose の呼び出しまたはロック解除がローカルの元の値で実行されます。  
  
 いくつかのシナリオでは、`using` または `lock` ブロックの結果として一時的なリソース リークが発生します。 1 つの例を次に示します。  
  
 `thisType f = null;`  
  
 `using (f)`  
  
 `{`  
  
 `f = new thisType();`  
  
 `...`  
  
 `}`  
  
 この場合、変数 `thisType` の元の値 \(null など\) は `using` ブロックが実行を終了するときに破棄されますが、ブロック内で作成された `thisType` オブジェクトは破棄されず、最終的にガベージ コレクションされます。  
  
 このエラーを解決するには、次の形式を使用します。  
  
 `using (thisType f = new thisType())`  
  
 `{`  
  
 `...`  
  
 `}`  
  
 この場合、新しく割り当てられた `thisType` オブジェクトが破棄されます。  
  
## 使用例  
 次のコードでは、警告 CS0728 が生成されます。  
  
```  
// CS0728.cs using System; public class ValidBase : IDisposable { public void Dispose() {  } } public class Logger { public static void dummy() { ValidBase vb = null; using (vb) { vb = null;  // CS0728 } vb = null; } public static void Main() { } }  
```