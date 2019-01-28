---
title: '方法: SharePoint コマンドの作成 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: da1b31b7cc1436c90437a9e2b5ef66adfee825b1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867898"
---
# <a name="how-to-create-a-sharepoint-command"></a>方法: SharePoint コマンドを作成します。
  SharePoint ツール拡張機能で、サーバー オブジェクト モデルを使用する場合は、カスタムを作成する必要があります*SharePoint コマンド*API を呼び出します。 SharePoint コマンドは、サーバー オブジェクト モデルを直接呼び出すことがアセンブリに定義します。  
  
 SharePoint コマンドの目的に関する詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)します。  
  
### <a name="to-create-a-sharepoint-command"></a>SharePoint コマンドを作成するには  
  
1.  次の構成があるクラス ライブラリ プロジェクトを作成します。  
  
    -   .NET Framework 3.5 を対象とします。 ターゲット フレームワークの選択の詳細については、次を参照してください。[方法.NET Framework のターゲット バージョンを指定する](../ide/how-to-target-a-version-of-the-dotnet-framework.md)」を参照してください。  
  
    -   X64、AnyCPU の対象プラットフォーム。 既定では、クラス ライブラリ プロジェクトのターゲット プラットフォームには AnyCPU です。 ターゲット プラットフォームを選択する方法についての詳細については、次を参照してください。[方法。プロジェクトを構成して対象プラットフォームを設定する](../ide/how-to-configure-projects-to-target-platforms.md)  
  
    > [!NOTE]  
    >  SharePoint コマンドは、.NET Framework 3.5 および SharePoint ツール拡張機能のターゲットをターゲットするため、SharePoint ツールの拡張機能を定義するのと同じプロジェクト内 SharePoint コマンドを実装することはできません、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]します。 別のプロジェクトで、拡張機能によって使用される任意の SharePoint コマンドを定義する必要があります。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  プロジェクトのクラスでは、SharePoint コマンドを定義するメソッドを作成します。 メソッドは、次のガイドラインに従う必要があります。  
  
    -   1 つまたは 2 つのパラメーターことができます。  
  
         最初のパラメーターである必要があります、<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>オブジェクト。 このオブジェクトは、Microsoft.SharePoint.SPSite またはコマンドを実行する Microsoft.SharePoint.SPWeb を提供します。 用意されています、<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger>をメッセージに書き込むために使用できるオブジェクト、**出力**ウィンドウまたは**エラー一覧**Visual Studio のウィンドウ。  
  
         2 番目のパラメーターは、任意の型を指定できますが、このパラメーターは省略可能です。 SharePoint ツールの拡張機能から、コマンドにデータを渡す必要がある場合は、SharePoint コマンドにこのパラメーターを追加できます。  
  
    -   戻り値を持つことができますが、これは省略可能です。  
  
    -   2 番目のパラメーターと戻り値は、Windows Communication Foundation (WCF) によってシリアル化できる型である必要があります。 詳細については、次を参照してください。[型は、データ コントラクト シリアライザーでサポートされている](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer)と[XmlSerializer クラスを使用して](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class)します。  
  
    -   メソッドは、可視性を持つことができます (**パブリック**、**内部**、または**プライベート**)、これは、静的または静的でないとします。  
  
4.  適用、<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>メソッドにします。 この属性は、このコマンドの一意の識別子を指定します。この識別子は、メソッド名と一致する必要はありません。  
  
     SharePoint ツールの拡張機能から、コマンドを呼び出すときに、同じ一意の識別子を指定する必要があります。 詳細については、「[方法 :SharePoint コマンドを実行](../sharepoint/how-to-execute-a-sharepoint-command.md)します。  
  
## <a name="example"></a>例  
 次のコード例は、識別子を持つ SharePoint コマンドを示します`Contoso.Commands.UpgradeSolution`します。 このコマンドは、デプロイ済みのソリューションにアップグレードするサーバー オブジェクト モデルでの Api を使用します。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]  
  
 最初の暗黙的なだけでなく<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>パラメーターでは、このコマンドはまた、SharePoint サイトにアップグレードされる .wsp ファイルの完全なパスを含むカスタムの文字列パラメーターが。 例のコンテキストでは、このコードを表示するには、次を参照してください。[チュートリアル。SharePoint プロジェクトのカスタム配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## <a name="deploying-the-command"></a>コマンドの配置  
 コマンドを展開するには、同じコマンド アセンブリを含める[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]拡張機能 (*vsix*) コマンドを使用して拡張機能のアセンブリにパッケージします。 Extension.vsixmanifest ファイル内のコマンドのアセンブリのエントリを追加することも必要があります。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [方法: SharePoint コマンドを実行します。](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [チュートリアル: Web パーツを表示するサーバー エクスプ ローラーを拡張します。](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
