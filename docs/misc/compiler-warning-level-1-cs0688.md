---
title: "コンパイラの警告 (レベル 1) CS0688 | Microsoft Docs"
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
  - "CS0688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0688"
ms.assetid: 8ce5af36-663e-46e8-87e9-bb32555796ae
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS0688
'method1' はリンク要求を含んでいますが、リンク要求を含んでいない 'method2' をオーバーライドまたは実装します。 セキュリティに問題が発生する可能性があります。  
  
 派生クラス メソッドに設定されているリンク要求は、基底クラス メソッドを呼び出すと簡単に迂回できます。 このセキュリティ ホールをふさぐには、基底クラス メソッドでもリンク要求を使用する必要があります。 詳しくは、「[Demand](http://msdn.microsoft.com/ja-jp/1ab877f2-70f4-4e0d-8116-943999dfe8f5) と[LinkDemand](http://msdn.microsoft.com/ja-jp/1ab877f2-70f4-4e0d-8116-943999dfe8f5)」をご覧ください。  
  
## 使用例  
 次の例では CS0688 が生成されます。 基底クラスを変更せずにこの警告を解決するには、オーバーライドするメソッドからセキュリティ属性を削除します。 この操作によって、セキュリティ上の問題は解決しません。  
  
```  
// CS0688.cs // compile with: /W:1 using System; using System.Security.Permissions; class Base { //Uncomment the following line to close the security hole //[FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] public virtual void DoScaryFileStuff() { } } class Derived: Base { [FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] // CS0688 public override void DoScaryFileStuff() { } static void Main() { } }  
```