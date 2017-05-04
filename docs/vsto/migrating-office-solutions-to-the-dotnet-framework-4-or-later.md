---
title: ".NET Framework 4 以降への Office ソリューションの移行 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Project.TargetFrameworkWarning"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Office プロジェクト [Visual Studio での Office 開発]、.NET Framework 4 への移行"
ms.assetid: 31f6c48b-c086-4362-8629-f644d6083a44
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# .NET Framework 4 以降への Office ソリューションの移行
  Office プロジェクトのターゲット フレームワークを旧バージョンの .NET Framework から [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、開発用コンピューターおよびエンド ユーザー コンピューターでソリューションを引き続き実行するために追加の手順が必要な場合があります。 詳細については、「[.NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトの実行に必要な変更](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)」を参照してください。  
  
 さらに、プロジェクトがコンパイルされなくなる場合があります。 Office プロジェクトの一部の機能は、.NET Framework のバージョンに応じてプログラミング モデルが異なっています。 Office プロジェクトのターゲット フレームワークを旧バージョンの .NET Framework から [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、プロジェクトに対して次のコード変更を加える必要があります。  
  
-   [.NET Framework 4 または .NET Framework 4.5 に移行する Excel プロジェクトおよび Word プロジェクトの更新](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [.NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトのリボンのカスタマイズの更新](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [.NET Framework 4 または .NET Framework 4.5 に移行する Outlook プロジェクトのフォーム領域の更新](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 Office プロジェクトのターゲット フレームワークは、そのプロジェクトを旧バージョンの Visual Studio からアップグレードすると変更されます。 詳細については、「[Office ソリューションのアップグレードと移行](../vsto/upgrading-and-migrating-office-solutions.md)」を参照してください。  
  
 対象が [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降であるときに、Office プロジェクトの一部の機能のプログラミング モデルが異なる理由の詳細については、「[.NET Framework 4 または .NET Framework 4.5 を対象とする Office プロジェクトのデザインの変更](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)」および「[Visual Studio Tools for Office Runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)」を参照してください。  
  
## 参照  
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)   
 [方法: .NET Framework のバージョンをターゲットにする](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)   
 [Office ソリューションのエラーのトラブルシューティング](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Office ソリューションのエラーについての追加サポート](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  