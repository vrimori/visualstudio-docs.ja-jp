---
title: ローカリゼーションのニュートラル リソース言語 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a9470718743e506a7a8cd5ad03d9b6f69b1d5477
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534994"
---
# <a name="neutral-resources-languages-for-localization"></a>ローカリゼーションのニュートラル リソース言語
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Resources.NeutralResourcesLanguageAttribute> クラスでは、メイン アセンブリに含まれるリソースのカルチャが指定されています。 この属性はパフォーマンス向上のために使われ、<xref:System.Resources.ResourceManager> オブジェクトがメイン アセンブリに含まれるリソースを検索しなくて済むようにします。  
  
 次のコードでは、ニュートラル リソース言語を設定する方法を示します。 このコードは、ビルド スクリプト、AssemblyInfo.vb または AssemblyInfo.cs に挿入できます。  
  
```vb  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```csharp  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Resources.ResourceManager>   
 [.NET Framework ベースの国際対応アプリケーションの概要](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [ローカリゼーション用リソースの階層編成](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [アプリケーションのローカライズ](../ide/localizing-applications.md)   
 [アプリケーションのグローバライズとローカライズ](../ide/globalizing-and-localizing-applications.md)

