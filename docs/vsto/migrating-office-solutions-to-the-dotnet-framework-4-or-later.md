---
title: ".NET Framework 4 以降に Office ソリューションの移行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8cb61186c7e8260578e9b69242c594c198f7e525
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>.NET Framework 4 以降への Office ソリューションの移行
  Office プロジェクトのターゲット フレームワークを旧バージョンの .NET Framework から [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、開発用コンピューターおよびエンド ユーザー コンピューターでソリューションを引き続き実行するために追加の手順が必要な場合があります。 詳細については、次を参照してください。[実行 Office プロジェクトは .NET Framework 4 または .NET Framework 4.5 に移行するのに必要な変更](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)です。  
  
 さらに、プロジェクトがコンパイルされなくなる場合があります。 Office プロジェクトの一部の機能は、.NET Framework のバージョンに応じてプログラミング モデルが異なっています。 Office プロジェクトのターゲット フレームワークを旧バージョンの .NET Framework から [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、プロジェクトに対して次のコード変更を加える必要があります。  
  
-   [更新の Excel および Word プロジェクトの .NET Framework 4 または .NET Framework 4.5 に移行します。](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [.NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトのリボンのカスタマイズの更新](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [.NET Framework 4 または .NET Framework 4.5 に移行する Outlook プロジェクトのフォーム領域の更新](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 Office プロジェクトのターゲット フレームワークは、そのプロジェクトを旧バージョンの Visual Studio からアップグレードすると変更されます。 詳細については、「 [Upgrading and Migrating Office Solutions](../vsto/upgrading-and-migrating-office-solutions.md)」を参照してください。  
  
 Office プロジェクトの一部の機能が対象とするさまざまなプログラミング モデルを持つ理由の詳細については、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]か、後で、「[デザインの Office プロジェクトの変更を .NET Framework 4 または .NET Framework 4.5を対象とします。](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)と[Visual Studio Tools for Office Runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)です。  
  
## <a name="see-also"></a>参照  
 [設計と、Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [方法: .NET Framework のバージョンをターゲットにする](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Office ソリューションのエラーのトラブルシューティング](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Office ソリューションのエラーについての追加サポート](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  