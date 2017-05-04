---
title: "How to: Create a SharePoint Command | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint commands [SharePoint development in Visual Studio], creating"
ms.assetid: e1fda8f0-eae1-4278-91c1-19a5e1fc327f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# How to: Create a SharePoint Command
  SharePoint ツールの拡張機能でサーバー オブジェクト モデルを使用する必要がある場合は、API を呼び出すためのカスタム *SharePoint コマンド*を作成する必要があります。  SharePoint コマンドは、サーバー オブジェクト モデルを直接呼び出すことができるアセンブリで定義します。  
  
 SharePoint コマンドの用途の詳細については、「[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)」を参照してください。  
  
### SharePoint コマンドを作成するには  
  
1.  次の構成のクラス ライブラリ プロジェクトを作成します。  
  
    -   .NET Framework 3.5 を対象とする構成  ターゲット フレームワークの選択の詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)」を参照してください。  
  
    -   AnyCPU または x64 プラットフォームを対象とする構成  既定では、クラス ライブラリ プロジェクトのターゲット プラットフォームは AnyCPU です。  ターゲット プラットフォームの選択の詳細については、「[NIB: How to: Optimize an Application for a Specific CPU Type](http://msdn.microsoft.com/ja-jp/294a75d2-4279-4b72-8298-2bea05be907a)」を参照してください。  
  
    > [!NOTE]  
    >  SharePoint コマンドは .NET Framework 3.5 を対象とし、SharePoint ツールの拡張機能は [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を対象としているため、SharePoint ツールの拡張機能を定義する同じプロジェクトに SharePoint コマンドを実装することはできません。  拡張機能で使用される SharePoint コマンドは、別のプロジェクトで定義する必要があります。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  プロジェクトのクラスに、SharePoint コマンドを定義するメソッドを作成します。  このメソッドは、次のガイドラインに準拠している必要があります。  
  
    -   パラメーターを 1 つまたは 2 つ持つことができること。  
  
         第 1 パラメーターは、<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> オブジェクトにする必要があります。  このオブジェクトは、コマンドが実行される Microsoft.SharePoint.SPSite または Microsoft.SharePoint.SPWeb を提供します。  また、Visual Studio の **\[出力\]** ウィンドウまたは **\[エラー一覧\]** ウィンドウへのメッセージの書き込みに使用できる <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> オブジェクトも提供します。  
  
         第 2 パラメーターは、任意の型にすることができ、省略可能です。  SharePoint ツールの拡張機能から SharePoint コマンドにデータを渡す必要がある場合に、このパラメーターを SharePoint コマンドに追加できます。  
  
    -   戻り値を返すことができること \(必須ではない\)。  
  
    -   第 2 パラメーターと戻り値に Windows Communication Foundation \(WCF\) でシリアル化できる型が使用されていること。  詳細については、「[データ コントラクト シリアライザーでサポートされる型](../Topic/Types%20Supported%20by%20the%20Data%20Contract%20Serializer.md)」および「[XmlSerializer クラスの使用](../Topic/Using%20the%20XmlSerializer%20Class.md)」を参照してください。  
  
    -   参照可能範囲 \(**public**、**internal**、または **private**\) を設定できること、および静的にも非静的にもできること。  
  
4.  <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> をメソッドに適用します。  この属性は、コマンドの一意識別子を指定します。この識別子がメソッド名と一致している必要はありません。  
  
     SharePoint ツールの拡張機能からコマンドを呼び出すときに、同じ一意識別子を指定する必要があります。  詳細については、「[How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)」を参照してください。  
  
## 例  
 `Contoso.Commands.UpgradeSolution` という識別子を持つ SharePoint コマンドを次のコード例に示します。  このコマンドは、サーバー オブジェクト モデルの API を使用して、配置したソリューションにアップグレードします。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#5)]  
  
 このコマンドには、暗黙の第 1 パラメーター <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> に加えて、SharePoint サイトにアップグレードされる .wsp ファイルの完全パスが含まれているカスタムの文字列パラメーターもあります。   このコードのコンテキストを確認するには、「[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)」を参照してください。  
  
## コードのコンパイル  
 この例は、次のアセンブリへの参照を必要とします。  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## コマンドの配置  
 コマンドを配置するには、コマンド アセンブリを、コマンドを使用する拡張機能アセンブリと同じ [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージに追加します。  また、コマンド アセンブリに対するエントリを extension.vsixmanifest ファイルに追加する必要もあります。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  