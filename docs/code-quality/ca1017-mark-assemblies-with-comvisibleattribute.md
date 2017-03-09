---
title: "CA1017: アセンブリに ComVisibleAttribute を設定します | Microsoft Docs"
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
  - "CA1017"
  - "MarkAssembliesWithComVisible"
helpviewer_keywords: 
  - "MarkAssembliesWithComVisible"
  - "CA1017"
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1017: アセンブリに ComVisibleAttribute を設定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 アセンブリには、それに適用される <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 属性がありません。  
  
## 規則の説明  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性によって、COM クライアントからマネージ コードにアクセスする方法を決定します。  アセンブリで COM の参照範囲を明示することをお勧めします。  COM の参照範囲は、アセンブリ全体に設定し、個々の型と型のメンバー用にオーバーライドできます。  この属性がない場合、アセンブリのコンテンツは COM クライアントから参照できます。  
  
## 違反の修正方法  
 この規則違反を修正するには、アセンブリにこの属性を追加します。  アセンブリを COM クライアントから参照できないようにするには、属性を適用し、属性値を `false` に設定します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  アセンブリを参照できるようにする場合、この属性を適用し、値を `true` に設定します。  
  
## 使用例  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性を適用したアセンブリを次の例に示します。例では、COM クライアントからこのアセンブリを参照できなくなります。  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-cs[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## 参照  
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [相互運用のための .NET 型の要件](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)