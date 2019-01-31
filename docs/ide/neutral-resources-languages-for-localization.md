---
title: ローカリゼーションのニュートラル リソース言語
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 513cd8295a3e25a171de6623ba706ce7dfb2a2e6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962106"
---
# <a name="neutral-resources-languages-for-localization"></a>ローカリゼーションのニュートラル リソース言語

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

- <xref:System.Resources.ResourceManager>
- [.NET Framework ベースの国際対応アプリケーションの概要](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)
- [ローカリゼーション用リソースの階層編成](../ide/hierarchical-organization-of-resources-for-localization.md)
- [アプリケーションのローカライズ](../ide/localizing-applications.md)
- [アプリケーションのグローバライズとローカライズ](../ide/globalizing-and-localizing-applications.md)