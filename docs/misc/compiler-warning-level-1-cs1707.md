---
title: "コンパイラの警告 (レベル 1) CS1707 | Microsoft Docs"
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
  - "CS1707"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1707"
ms.assetid: 47b6096e-4e4b-4057-b9d7-4a096139267a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS1707
新しい言語規則のために、'MethodName2' の代わりに 'MethodName1' にバインドされたデリゲート 'DelegateName' です  
  
 C\# 2.0 では、デリゲートのメソッドへのバインドに新しい規則が導入されました。 従来は無視されていた追加情報が考慮されます。 この警告は、デリゲートが従来とは異なるメソッドのオーバーロードにバインドされていることを示しています。 このデリゲートが 'MethodName2' ではなく 'MethodName1' にバインドされることが適切かどうかを確認してください。  
  
 デリゲートのバインド先のメソッドをコンパイラがどのように判断するかについては、「[デリゲートの分散の使用](../Topic/Using%20Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。