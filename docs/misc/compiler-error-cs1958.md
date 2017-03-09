---
title: "コンパイラ エラー CS1958 | Microsoft Docs"
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
  - "CS1958"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1958"
ms.assetid: bb6f3bb2-ea93-4d2e-984c-da9c99f5653f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1958
オブジェクトとコレクションの初期化子式は、デリゲートの作成式には適用できません  
  
 デリゲートには、クラスや構造体に含まれるようなメンバーはありません。したがって、オブジェクト初期化子で初期化するものはありません。 このエラーが発生する場合、おそらく、デリゲート作成式の後に中かっこがあることが原因です。 中かっこを削除するだけで、このエラーは発生しなくなります。  
  
### このエラーを解決するには  
  
1.  中かっこを削除します。  
  
## 使用例  
 次のコードではCS1958 が生成されます。  
  
```  
// cs1958.cs public class MemberInitializerTest { delegate void D<T>(); public static void GenericMethod<T>() { } public static void Run() { D<int> genD = new D<int>(GenericMethod<int>) { }; // CS1958 // Try the following line instead // D<int> genD = new D<int>(GenericMethod<int>); } }  
```