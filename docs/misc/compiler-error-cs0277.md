---
title: "コンパイラ エラー CS0277 | Microsoft Docs"
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
  - "CS0277"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0277"
ms.assetid: 8abec3eb-4d4c-4aab-87cc-d0444ab23535
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0277
'class' はインターフェイス メンバー 'accessor' を実装しません。 'class accessor' は public ではありません  
  
 このエラーは、インターフェイスのプロパティを実装しようとしたときに、クラス内のプロパティ アクセサーの実装がパブリックではない場合に生じます。 インターフェイス メンバーを実装するメソッドには、パブリック アクセシビリティが必要です。 解決するには、プロパティ アクセサーのアクセス修飾子を削除します。  
  
## 使用例  
 次の例では、CS0277 が生成されます。  
  
```  
// CS0277.cs public interface MyInterface { int Property { get; set; } } public class MyClass : MyInterface   // CS0277 { public int Property { get { return 0; } // Try this instead: //set { } protected set { } } }  
```