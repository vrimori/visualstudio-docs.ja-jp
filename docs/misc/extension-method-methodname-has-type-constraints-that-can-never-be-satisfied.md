---
title: "拡張メソッド &#39;&lt;methodname&gt;&#39; に、満たされる可能性のない型制約があります | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36561"
  - "vbc36561"
helpviewer_keywords: 
  - "BC36561"
ms.assetid: ff42d6e9-611b-407d-a269-f268b36ed277
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 拡張メソッド &#39;&lt;methodname&gt;&#39; に、満たされる可能性のない型制約があります
このメソッドの型パラメーターは、満たされることが妨げられる仕方で相互作用します。 次の拡張メソッドは、例を示します。  
  
```  
'' Not valid. '<Extension()> _ 'Sub extensionExample(Of T As U, U)(ByVal para1 As T, ByVal para2 As U) 'End Sub  
```  
  
 メソッドは拡張メソッドであるため、コンパイラは、メソッドの宣言の最初のパラメーター、`para1`、およびそのパラメーターに渡される引数によってのみ、メソッドを拡張するデータ型を決定できる必要があります。 最初のパラメーターがジェネリック型パラメーター、`para1 as T` を参照するとき、ジェネリック パラメーターの制約は、メソッドを適用する型のセットを制限します。  
  
 拡張メソッドの適用性は最初のパラメーターに指定された引数から判断されます。次のコードでは `arg1` が相当します。  
  
 `'' Not valid.`  
  
 `'arg1.extensionExample(arg2)`  
  
 最初の引数  `arg1` だけを見て、最初のパラメーター `para1` で参照されるすべてのジェネリック型パラメーターの制約を確認できる必要があります。`extensionExample` では、最初のパラメーターだけでは、拡張されている型のセットを特定できません。 型パラメーター `T` は型パラメーター `U` によって制約されますが、これは `para1` によって参照されず、`arg1` から推測できません。 したがって、可能な型へのメソッドの適用性を確認することはできず、このメソッドを呼び出すことはできません。  
  
 **エラー ID:** BC36561  
  
### このエラーを解決するには  
  
-   型の宣言を変更して、型の間で相互依存の状態をなくします。  
  
## 参照  
 [拡張メソッド](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)