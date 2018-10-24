---
title: メイン アセンブリおよびローカライズされたサテライト アセンブリのバージョン番号
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cbc74d746453c5d8e60161004a5b56a2c21915dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882604"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>メイン アセンブリおよびローカライズされたサテライト アセンブリのバージョン番号
<xref:System.Resources.SatelliteContractVersionAttribute> クラスは、リソース マネージャーでローカライズされたリソースを使用するメイン アセンブリのバージョン管理をサポートしています。 <xref:System.Resources.SatelliteContractVersionAttribute> をアプリケーションのメイン アセンブリに適用すると、サテライト アセンブリを更新することなくメイン アセンブリを更新したり、再展開したりできます。 たとえば、新しいリソースを導入していない Service Pack でも、サテライト アセンブリをリビルドして再展開することなく <xref:System.Resources.SatelliteContractVersionAttribute> クラスを使用できます。 ローカライズされたリソースを使用できるようにするには、メイン アセンブリのサテライト コントラクト バージョンがサテライト アセンブリの <xref:System.Reflection.AssemblyVersionAttribute> クラスと一致する必要があります。 <xref:System.Resources.SatelliteContractVersionAttribute> に正確なバージョン番号を指定します。"*" などのワイルドカード文字は使用できません。 詳細については、[リソースの取得](/dotnet/framework/resources/retrieving-resources-in-desktop-apps)に関するページを参照してください。

## <a name="update-assemblies"></a>アセンブリを更新する
 <xref:System.Resources.SatelliteContractVersionAttribute> クラスを使用すると、サテライト アセンブリを更新することなくメイン アセンブリを更新し、メイン アセンブリを更新することなくサテライト アセンブリを更新できます。 メイン アセンブリを更新すると、メイン アセンブリのバージョン番号は変更されます。 既存のサテライト アセンブリを引き続き使用する場合は、メイン アセンブリのバージョン番号を変更し、サテライト コントラクト バージョン番号は同じままにします。 たとえば、最初のリリースで、メイン アセンブリのバージョンが 1.0.0.0 だとします。 サテライト アセンブリのサテライト コントラクト バージョンとアセンブリ バージョンはいずれも 1.0.0.0 です。 Service Pack に合わせてメイン アセンブリを更新する必要がある場合は、アセンブリのバージョンを 1.0.0.1 に変更し、サテライト コントラクト バージョンとサテライトのアセンブリ バージョンは 1.0.0.0 のままにすることができます。

 サテライト アセンブリを更新する必要があり、メイン アセンブリの更新は不要な場合は、サテライト アセンブリの <xref:System.Reflection.AssemblyVersionAttribute> を変更します。 サテライト アセンブリと共に、新しいサテライト アセンブリが古いサテライト アセンブリと互換性があることを示すポリシー アセンブリを含めて出荷する必要があります。 ポリシーの詳細については、「[ランタイムがアセンブリを検索する方法](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)」を参照してください。

 次のコードは、サテライト コントラクト バージョンを設定する方法を示しています。 このコードは、ビルド スクリプト、*AssemblyInfo.vb* または *AssemblyInfo.cs* に挿入できます。

```vb
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>
```

```csharp
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]
```

## <a name="see-also"></a>関連項目

- [ランタイムがアセンブリを検索する方法](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [アセンブリ属性の設定](/dotnet/framework/app-domains/set-assembly-attributes)
- [セキュリティおよびローカライズされたサテライト アセンブリ](../ide/security-and-localized-satellite-assemblies.md)
- [アプリケーションをローカライズする](../ide/localizing-applications.md)
- [アプリケーションのグローバライズとローカライズ](../ide/globalizing-and-localizing-applications.md)