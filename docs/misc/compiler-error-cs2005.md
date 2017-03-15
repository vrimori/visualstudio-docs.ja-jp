---
title: "コンパイラ エラー CS2005 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS2005"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2005"
ms.assetid: 03535d2a-ae30-4272-ab45-e277df5ee8e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS2005
'option' オプションのファイルが指定されていません。  
  
 [コンパイラ オプション](/dotnet/csharp/language-reference/compiler-options/index)が、一部のみ指定されました。  
  
 たとえば、[\/recurse](/dotnet/csharp/language-reference/compiler-options/recurse-compiler-option) を使用する場合、**\/recurse:***filename***.cs** のように、検索対象のファイルを指定する必要があります。  
  
## 使用例  
 次の例では CS2005 が生成されます。  
  
```  
// CS2005.cs // compile with: /recurse: // CS2005 expected class x { public static void Main() {} }  
```