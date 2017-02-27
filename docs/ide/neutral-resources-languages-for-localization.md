---
title: "ローカリゼーションのニュートラル リソース言語 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "カルチャ, 検索 (リソースを)"
  - "グローバリゼーション [Visual Studio], リソース"
  - "ローカリゼーション [Visual Studio], リソース"
  - "ニュートラル リソース"
  - "NeutralResourcesLanguageAttribute クラス"
  - "リソース [Visual Studio], フォールバック システム"
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# ローカリゼーションのニュートラル リソース言語
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:System.Resources.NeutralResourcesLanguageAttribute> クラスは、メイン アセンブリに含まれるリソースのカルチャを指定します。  この属性はパフォーマンス向上のために使用します。これにより、<xref:System.Resources.ResourceManager> オブジェクトがメイン アセンブリに含まれたリソースを検索しなくなります。  
  
 ニュートラル リソース言語を設定する方法を次のコードに示します。  このコードは、ビルド スクリプトに配置することも、AssemblyInfo.vb ファイルまたは AssemblyInfo.cs ファイルに配置することもできます。  
  
```vb#  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```c#  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## 参照  
 <xref:System.Resources.ResourceManager>   
 [.NET Framework ベースの国際対応アプリケーションの概要](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [ローカリゼーション用リソースの階層編成](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [アプリケーションのローカライズ](../ide/localizing-applications.md)   
 [アプリケーションのグローバライズとローカライズ](../ide/globalizing-and-localizing-applications.md)