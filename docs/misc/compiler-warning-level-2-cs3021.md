---
title: "コンパイラの警告 (レベル 2) CS3021 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3021"
ms.assetid: 89f09e4d-65b0-4422-86ea-85c7e05ac29b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS3021
アセンブリに CLSCompliant 属性が含まれていないため、'type' には CLSCompliant 属性が必要ありません  
  
 アセンブリ レベルの CLSCompliant 属性が true に設定されてないアセンブリ内 \(つまり、行 `[assembly: CLSCompliant(true)]`\) のクラスに `[CLSCompliant(false)]`  がある場合に、この警告が生じます。 アセンブリは自らを CLS 準拠と宣言していないため、非準拠であると見なされます。そのため、アセンブリ内では非準拠を宣言する必要はありません。 CLS 準拠について詳しくは、「[CLS 準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)」をご覧ください。  
  
 この警告を消去するには、対象属性を削除するか、アセンブリ レベルの属性を追加します。  
  
## 使用例  
 次の例では、CS3021 エラーが生成されます。  
  
```  
// CS3021.cs using System; // Uncomment the following line to declare the assembly CLS Compliant, // and avoid the warning without removing the attribute on the class. //[assembly: CLSCompliant(true)] // Remove the next line to avoid the warning. [CLSCompliant(false)]               // CS3021 public class C { public static void Main() { } }  
```  
  
## 参照  
 [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)