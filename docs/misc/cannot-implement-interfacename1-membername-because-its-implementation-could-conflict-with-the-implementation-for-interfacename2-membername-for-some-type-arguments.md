---
title: "&#39;&lt;interfacename1&gt;.&lt;membername&gt;&#39; を実装できません。実装すると、&#39;&lt;interfacename2&gt;.&lt;membername&gt;&#39; の実装との間で型引数に関する競合が発生する可能性があります | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32125"
  - "vbc32125"
helpviewer_keywords: 
  - "BC32125"
ms.assetid: 74321d27-4ff8-440c-b5de-d67e98fff274
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;interfacename1&gt;.&lt;membername&gt;&#39; を実装できません。実装すると、&#39;&lt;interfacename2&gt;.&lt;membername&gt;&#39; の実装との間で型引数に関する競合が発生する可能性があります
クラスで 2 つ以上のジェネリック インターフェイスが実装され、その 1 つがもう 1つを継承しているために、インターフェイス メンバーの 2 つの実装が特定の型引数の値で衝突する可能性があります。  
  
 次のステートメントでは、このエラーが生成される可能性があります。  
  
```  
Public Interface iFace1(Of t) Sub testSub() End Interface Public Interface iFace2(Of u) Inherits iFace1(Of u) End Interface Public Class testClass(Of y, z) Implements iFace1(Of y), iFace2(Of z) Public Sub testSuby() Implements iFace1(Of y).testSub End Sub Public Sub testSubz() Implements iFace1(Of z).testSub End Sub End Class  
```  
  
 `iFace2` は独自の型パラメーター \(`u`\) を使用して `iFace1` を継承しているため、同じ型引数が `y` と `z` に渡された場合、`testClass` は同じシグネチャを持つ 2 つのバージョンの `iFace1.testSub` を実装します。 この場合、アクセスするバージョンがあいまいになる可能性があります。  
  
 **エラー ID:** BC32125  
  
### このエラーを解決するには  
  
-   `iFace1` が 2 つの異なる型引数で実装されないように、インターフェイスの継承構造を変更します。  
  
     または  
  
-   実装の競合の原因となるインターフェイスのいずれか 1 つを `Implements` ステートメントから削除します。  
  
## 参照  
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [ビルド内にありません: Implements キーワードおよび Implements ステートメント](http://msdn.microsoft.com/ja-jp/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)