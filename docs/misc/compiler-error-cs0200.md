---
title: "コンパイラ エラー CS0200 | Microsoft Docs"
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
  - "CS0200"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0200"
ms.assetid: 1990704a-edfa-4dbd-8477-d9c7aae58c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0200
プロパティまたはインデクサー 'property' は読み取り専用なので、割り当てることはできません  
  
 [property](/dotnet/csharp/programming-guide/classes-and-structs/using-properties) に値を代入しようとしましたが、property には set アクセサーはありません。 set アクセサーを追加してエラーを解決します。 詳細については、「[方法: 読み取り\/書き込みのプロパティの宣言と使用](../Topic/How%20to:%20Declare%20and%20Use%20Read%20Write%20Properties%20\(C%23%20Programming%20Guide\).md)」を参照してください。  
  
## 使用例  
 次の例では CS0200 が生成されます。  
  
```  
// CS0200.cs public class MainClass { // private int _mi; int I { get { return 1; } // uncomment the set accessor and declaration for _mi /* set { _mi = value; } */ } public static void Main () { MainClass II = new MainClass(); II.I = 9;   // CS0200 } }  
```