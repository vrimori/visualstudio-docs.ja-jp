---
title: "コンパイラの警告 (レベル 1) CS1570 | Microsoft Docs"
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
  - "CS1570"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1570"
ms.assetid: a121d5c4-8b90-4cda-af5b-6ba8f23b2b1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS1570
'construct' の XML コメントの XML 形式が正しくありません \- 'reason'  
  
 [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option) を使用する場合、ソース コード内のコメントは XML で記述する必要があります。 XML マークアップにエラーがあると、CS1570 が生成されます。 例:  
  
-   [\<exception\>](../Topic/%3Cexception%3E%20\(C%23%20Programming%20Guide\).md) タグなどで文字列を **cref** に渡す場合は、文字列を二重引用符で囲む必要があります。  
  
-   終了タグのない [\<seealso\>](../Topic/%3Cseealso%3E%20\(C%23%20Programming%20Guide\).md) などのタグを使用する場合は、終わり山かっこの前にスラッシュを指定する必要があります。  
  
-   より大記号またはより小記号を説明のテキストで使用する必要がある場合は、これらの記号を **&gt;** または **&lt;** で表現する必要があります。  
  
-   [\<include\>](../Topic/%3Cinclude%3E%20\(C%23%20Programming%20Guide\).md) タグのファイル属性またはパス属性がないか、正しくない形式です。  
  
 次の例では CS1570 が生成されます。  
  
```  
// CS1570.cs // compile with: /W:1 namespace ns { // the following line generates CS1570 /// <summary> returns true if < 5 </summary> // try this instead // /// <summary> returns true if <5 </summary> public class MyClass { public static void Main () { } } }  
```