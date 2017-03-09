---
title: "コンパイラの警告 (レベル 1) CS1584 | Microsoft Docs"
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
  - "CS1584"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1584"
ms.assetid: 56c8f9bf-4cce-4269-b573-d60e5b11f9ab
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS1584
'member' の XML コメントで、cref 属性 'invalid\_syntax' の構文が正しくありません。  
  
 ドキュメント コメント用タグに渡されるパラメーターのいずれかの構文が正しくありません。 詳細については、「[ドキュメント コメントとして推奨されるタグ](/dotnet/csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments)」を参照してください。  
  
## 使用例  
 次の例では CS1584 が生成されます。  
  
```  
// CS1584.cs // compile with: /W:1 /doc:CS1584.xml /// <remarks>Test class</remarks> public class Test { /// <remarks>Called in <see cref="Test.Mai()n"/>.</remarks>   // CS1584 // try the following line instead // /// <remarks>Called in <see cref="Test.Main()"/>.</remarks> public static void Test2() {} /// <remarks>Main method</remarks> public static void Main() {} }  
```