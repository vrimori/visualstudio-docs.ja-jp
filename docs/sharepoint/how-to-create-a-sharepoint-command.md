---
title: '方法: SharePoint コマンドを作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fbfaeba966a2608f67ff63b0de39f13669a7169f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-sharepoint-command"></a>方法: SharePoint コマンドを作成する
  を SharePoint ツール拡張機能で、サーバー オブジェクト モデルを使用する場合は、カスタムを作成する必要があります*SharePoint コマンド*API を呼び出すためです。 SharePoint コマンドは、サーバー オブジェクト モデルを直接呼び出すことができるアセンブリで定義します。  
  
 SharePoint コマンドの目的に関する詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)です。  
  
### <a name="to-create-a-sharepoint-command"></a>SharePoint コマンドを作成するには  
  
1.  次の構成を持つクラス ライブラリ プロジェクトを作成します。  
  
    -   .NET Framework 3.5 を対象とします。 詳細については、ターゲット フレームワークを選択すると、次を参照してください。[する方法: .NET Framework のバージョンを対象に](../ide/how-to-target-a-version-of-the-dotnet-framework.md)です。  
  
    -   X64、AnyCPU をターゲット プラットフォーム。 既定では、クラス ライブラリ プロジェクトのターゲット プラットフォームは AnyCPU です。 詳細については、ターゲット プラットフォームを選択すると、次を参照してください。[する方法: プロジェクトのターゲット プラットフォームを構成](../ide/how-to-configure-projects-to-target-platforms.md)です。  
  
    > [!NOTE]  
    >  SharePoint コマンドは、.NET Framework 3.5 と SharePoint ツールの拡張機能のターゲットをターゲットために、SharePoint ツール拡張を定義するのと同じプロジェクトでの SharePoint コマンドを実装することはできません、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]です。 別のプロジェクトで拡張機能によって使用されている SharePoint コマンドを定義する必要があります。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  クラスでは、プロジェクトで、SharePoint コマンドを定義するメソッドを作成します。 メソッドは、次のガイドラインに従う必要があります。  
  
    -   パラメーター 1 つまたは 2 つ持つことができます。  
  
         最初のパラメーターである必要があります、<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>オブジェクト。 このオブジェクトは、Microsoft.SharePoint.SPSite またはコマンドを実行する Microsoft.SharePoint.SPWeb を提供します。 用意されています、<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger>にメッセージを書き込むために使用できるオブジェクト、**出力**ウィンドウまたは**エラー一覧**Visual Studio のウィンドウ。  
  
         2 番目のパラメーターは、任意の型を指定できますが、このパラメーターは省略可能。 SharePoint コマンドにこのパラメーターを追加するには、SharePoint ツールの拡張機能から、コマンドにデータを渡す必要がある場合。  
  
    -   戻り値を持つことができますが、これは省略可能です。  
  
    -   2 番目のパラメーターと戻り値は、Windows Communication Foundation (WCF) によってシリアル化できる型である必要があります。 詳細については、次を参照してください。[データ コントラクト シリアライザーでサポートされる型](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer)と[XmlSerializer クラスを使用して](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class)です。  
  
    -   メソッドは、可視性を持つことができます (**パブリック**、**内部**、または**プライベート**)、および静的か非静的であることができます。  
  
4.  適用、<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>メソッドにします。 この属性は、コマンドの一意の識別子を指定します。この識別子は、メソッド名と一致する必要はありません。  
  
     SharePoint ツールの拡張機能から、コマンドを呼び出す場合は、同じ一意の識別子を指定する必要があります。 詳細については、次を参照してください。[する方法: SharePoint コマンドを実行](../sharepoint/how-to-execute-a-sharepoint-command.md)です。  
  
## <a name="example"></a>例  
 次のコード例は、識別子を持つ SharePoint コマンドを示します`Contoso.Commands.UpgradeSolution`です。 このコマンドでは、サーバー オブジェクト モデルの Api を使用して、配置されたソリューションをアップグレードします。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]  
  
 最初の暗黙的なだけでなく<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>パラメーター、このコマンドも、カスタム文字列パラメーターが含まれて、SharePoint サイトにアップグレードされている .wsp ファイルの完全なパスが含まれています。 このコード例のコンテキストを参照してください[チュートリアル: SharePoint プロジェクトのカスタム配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## <a name="deploying-the-command"></a>コマンドの配置  
 コマンドを展開するには、同じコマンド アセンブリを含める[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]コマンドを使用する拡張機能のアセンブリに拡張機能 (VSIX) にパッケージ化します。 また、コマンド内のアセンブリになる extension.vsixmanifest ファイル エントリを追加する必要があります。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint オブジェクト モデルの呼び出し](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [方法: SharePoint コマンドを実行](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [チュートリアル: サーバー エクスプローラーを拡張して Web パーツを表示する](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  