---
title: "CA2221: ファイナライザーは保護されなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2221"
  - "FinalizersShouldBeProtected"
helpviewer_keywords: 
  - "CA2221"
  - "FinalizersShouldBeProtected"
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2221: ファイナライザーは保護されなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FinalizersShouldBeProtected|  
|CheckId|CA2221|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 パブリック型で、ファミリ \(保護された\) アクセスを指定していないファイナライザーを実装しています。  
  
## 規則の説明  
 ファイナライザーは、ファミリ アクセス修飾子を使用する必要があります。  この規則は、C\#、Visual Basic、および Visual C\+\+ コンパイラで必須です。  
  
## 違反の修正方法  
 この規則違反を修正するには、ファイナライザーをファミリ アクセスできるように変更します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 高水準の .NET 言語でこの規則違反は発生しません。Microsoft Intermediate Language \(MSIL\) を記述している場合は、発生することがあります。  
  
```  
// =============== CLASS MEMBERS DECLARATION ===================  
//   note that class flags, 'extends' and 'implements' clauses  
//          are provided here for information only  
  
.namespace UsageLibrary  
{  
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected  
         extends [mscorlib]System.Object  
  {  
    .method public hidebysig instance void  
            Finalize() cil managed  
    {  
  
      // Code size       1 (0x1)  
      .maxstack  0  
      IL_0000:  ret  
    } // end of method FinalizeMethodNotProtected::Finalize  
  
    .method public hidebysig specialname rtspecialname  
            instance void  .ctor() cil managed  
    {  
      // Code size       7 (0x7)  
      .maxstack  1  
      IL_0000:  ldarg.0  
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()  
      IL_0006:  ret  
    } // end of method FinalizeMethodNotProtected::.ctor  
  
  } // end of class FinalizeMethodNotProtected  
} // end of namespace  
```  
  
## 参照  
 [Dispose パターン](../Topic/Dispose%20Pattern.md)