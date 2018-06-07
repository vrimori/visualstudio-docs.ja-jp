---
title: .NET Framework 4 以降に Office ソリューションの移行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ac244bebb1a625c7858a62399ee79126e309cf2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571800"
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>Office ソリューションの移行、.NET Framework 4 以降
  Office プロジェクトのターゲット フレームワークを旧バージョンの .NET Framework から [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、開発用コンピューターおよびエンド ユーザー コンピューターでソリューションを引き続き実行するために追加の手順が必要な場合があります。 詳細については、次を参照してください。 [、.NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトを実行する変更が必要に](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)です。  
  
 さらに、プロジェクトがコンパイルされなくなる場合があります。 Office プロジェクトの一部の機能は、.NET Framework のバージョンに応じてプログラミング モデルが異なっています。 Office プロジェクトのターゲット フレームワークを旧バージョンの .NET Framework から [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、プロジェクトに対して次のコード変更を加える必要があります。  
  
-   [.NET Framework 4 または .NET Framework 4.5 に移行する Excel および Word のプロジェクトを更新します。](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [.NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトのリボンのカスタマイズを更新します。](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [.NET Framework 4 または .NET Framework 4.5 に移行する Outlook プロジェクトのフォーム領域を更新します。](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 Office プロジェクトのターゲット フレームワークは、そのプロジェクトを旧バージョンの Visual Studio からアップグレードすると変更されます。 詳細については、次を参照してください。[アップグレードし、Office ソリューションの移行](../vsto/upgrading-and-migrating-office-solutions.md)です。  
  
 Office プロジェクトの一部の機能が対象とするさまざまなプログラミング モデルを持つ理由の詳細については、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]か、後で、「[を .NET Framework 4 または .NET Framework 4.5対象とするOfficeプロジェクトデザインの変更](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)と[Visual Studio Tools for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)です。  
  
## <a name="see-also"></a>関連項目  
 [設計および Office ソリューションを作成します。](../vsto/designing-and-creating-office-solutions.md)   
 [方法: .NET Framework のバージョンを対象](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Office ソリューションのエラーをトラブルシューティングします。](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Office ソリューションのエラーについての追加サポート](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  