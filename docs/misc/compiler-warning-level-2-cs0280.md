---
title: "コンパイラの警告 (レベル 2) CS0280 | Microsoft Docs"
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
  - "CS0280"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0280"
ms.assetid: 9b453478-92aa-4fd2-9b87-780fd138603a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS0280
'type' は、'pattern name' パターンを実装しません。 'method name' には正しくないシグネチャが含まれます。  
  
 C\# の 2 つのステートメント **foreach** と **using** が、定義済みのパターン "collection" および "resource" にそれぞれ依存します。 この警告は、メソッドのシグネチャが正しくないために、コンパイラがこれらのステートメントのいずれかをそのパターンに一致させることができない場合に発生します。 たとえば、"collection" パターンには、パラメーターを受け取らず、`boolean` を返す <xref:System.Collections.IEnumerator.MoveNext%2A> と呼ばれるメソッドがある必要があります。 パラメーターを持つか、オブジェクトを返す <xref:System.Collections.IEnumerator.MoveNext%2A> メソッドがコードに含まれている可能性があります。  
  
 "resource" パターンと `using` は別の例を提供します。 "resource" パターンには <xref:System.IDisposable.Dispose%2A> メソッドが必要です。同じ名前のプロパティを定義した場合、この警告が表示されます。  
  
 この警告を解決するには、型のメソッド シグネチャがパターンの対応するメソッドのシグネチャと一致することを確認し、パターンに必要なメソッドと同じ名前のプロパティがないことを確認します。  
  
## 使用例  
 次の例では CS0280 が生成されます。  
  
```  
// CS0280.cs using System; using System.Collections; public class ValidBase: IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } } class Derived : ValidBase { // field, not method new public int GetEnumerator; } public class Test { public static void Main() { foreach (int i in new Derived()) {}   // CS0280 } }  
```