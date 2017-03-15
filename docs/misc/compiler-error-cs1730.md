---
title: "コンパイラ エラー CS1730 | Microsoft Docs"
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
  - "CS1730"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1730"
ms.assetid: 20900ca0-702f-4f35-9a60-2dee9cb11902
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1730
アセンブリ属性とモジュール属性は、句および extern エイリアス宣言を使用する場合を除き、ファイルで定義された他のすべての要素の前に指定しなければなりません  
  
 アセンブリ レベルで適用された属性は、どの型定義の後にも指定できません。  
  
### このエラーを解決するには  
  
1.  属性を、ファイルの上部に移動しますが、`using` ディレクティブと `extern` エイリアス宣言の下に配置します。  
  
## 使用例  
 次のコードでは CS1730 が生成されます。  
  
```  
// cs1730.cs class Test { } [assembly: System.Attribute] // CS1730  
```  
  
## 参照  
 [属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)