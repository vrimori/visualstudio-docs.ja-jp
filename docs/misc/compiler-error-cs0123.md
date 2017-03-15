---
title: "コンパイラ エラー CS0123 | Microsoft Docs"
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
  - "CS0123"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0123"
ms.assetid: 57be2c58-6d87-40af-9376-cd7f91023044
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0123
デリゲート 'delegate' に一致する 'method' のオーバーロードはありません  
  
 デリゲートの作成を試みましたが、正しいシグネチャを使用しなかったために失敗しました。 デリゲートのインスタンスは、デリゲート宣言と同じシグネチャを使用して宣言する必要があります。  
  
 このエラーは、メソッドまたはデリゲートのシグネチャを調整すれば解決できます。 詳細については、「[デリゲート](/dotnet/csharp/programming-guide/delegates/index)」を参照してください。  
  
 次の例では CS0123 が生成されます。  
  
```  
// CS0123.cs delegate void D(); delegate void D2(int i); public class C { public static void f(int i) {} public static void Main() { D d = new D(f);   // CS0123 D2 d2 = new D2(f);   // OK } }  
```