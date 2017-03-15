---
title: "CA1016: アセンブリに AssemblyVersionAttribute を設定します | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkAssembliesWithAssemblyVersion"
  - "CA1016"
helpviewer_keywords: 
  - "CA1016"
  - "MarkAssembliesWithAssemblyVersion"
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1016: アセンブリに AssemblyVersionAttribute を設定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithAssemblyVersion|  
|CheckId|CA1016|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 アセンブリにバージョン番号がありません。  
  
## 規則の説明  
 アセンブリの ID は次の情報で構成されます。  
  
-   アセンブリ名  
  
-   バージョン番号  
  
-   カルチャ  
  
-   公開キー \(厳密名のアセンブリ\)  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] では、バージョン番号を使用してアセンブリを一意に識別し、厳密な名前を持つアセンブリの型にバインドします。  バージョン番号は、バージョンと発行者のポリシーと共に使用されます。  既定で、アプリケーションは、ビルドされたアセンブリのバージョンでのみ実行されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> 属性を使用してアセンブリにバージョン番号を追加します。  次の例を参照してください。  
  
## 警告を抑制する状況  
 アセンブリがサード パーティによって使用される場合、または稼動環境で使用される場合は、この規則による警告を抑制しないでください。  
  
## 使用例  
 <xref:System.Reflection.AssemblyVersionAttribute> 属性を適用したアセンブリを次の例に示します。  
  
 [!code-cs[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## 参照  
 [アセンブリのバージョン管理](../Topic/Assembly%20Versioning.md)   
 [方法 : 発行者ポリシーを作成する](../Topic/How%20to:%20Create%20a%20Publisher%20Policy.md)