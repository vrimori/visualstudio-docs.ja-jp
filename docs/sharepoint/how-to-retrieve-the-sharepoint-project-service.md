---
title: "方法: SharePoint プロジェクト サービスの取得 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint project service
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b1abdf4a48d05285a7394469dd391caf48981f9f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>方法: SharePoint プロジェクト サービスを取得する
  次の種類のソリューションで SharePoint プロジェクト サービスにアクセスすることができます。  
  
-   プロジェクトの拡張機能、プロジェクト項目の拡張機能、またはプロジェクト項目の種類の定義など、SharePoint プロジェクト システムの拡張機能です。 これらの種類の拡張機能の詳細については、次を参照してください。 [SharePoint プロジェクト システムを拡張する](../sharepoint/extending-the-sharepoint-project-system.md)です。  
  
-   拡張機能、 **SharePoint 接続**内のノード**サーバー エクスプ ローラー**です。 これらの種類の拡張機能の詳細については、次を参照してください。[サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張する](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)です。  
  
-   VSPackage など、Visual Studio 拡張機能の別の型。  
  
## <a name="retrieving-the-service-in-project-system-extensions"></a>プロジェクト システムの拡張機能でのサービスの取得  
 SharePoint プロジェクト システムの拡張機能でを使用してプロジェクト サービスにアクセスすることができます、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>オブジェクト。  
  
 次の手順を使用して、プロジェクト サービスを取得することもできます。  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>プロジェクトの拡張機能でサービスを取得するには  
  
1.  実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>インターフェイスでは、検索、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>メソッドです。  
  
2.  使用して、 *projectService*サービスにアクセスするパラメーターです。  
  
     次のコード例は、プロジェクト サービスを使用してメッセージを記述する方法を示します、**出力**ウィンドウと**エラー一覧**単純なプロジェクトの拡張機能 ウィンドウ。  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     プロジェクトの拡張機能の作成の詳細については、次を参照してください。[する方法: SharePoint プロジェクトの拡張機能を作成する](../sharepoint/how-to-create-a-sharepoint-project-extension.md)です。  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>プロジェクト項目の拡張機能でサービスを取得するには  
  
1.  実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>インターフェイスでは、検索、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>メソッドです。  
  
2.  使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A>のプロパティ、 *projectItemType*サービスを取得するパラメーターです。  
  
     次のコード例は、プロジェクト サービスを使用してメッセージを記述する方法を示します、**出力**ウィンドウと**エラー一覧**の簡単な拡張機能にウィンドウ、**リスト定義**プロジェクト項目です。  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     プロジェクト項目の拡張機能の作成の詳細については、次を参照してください。[する方法: SharePoint プロジェクト項目の拡張機能を作成する](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)です。  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>プロジェクト項目の種類の定義でサービスを取得するには  
  
1.  実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>インターフェイスでは、検索、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>メソッドです。  
  
2.  使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A>のプロパティ、 *typeDefinition*サービスを取得するパラメーターです。  
  
     次のコード例は、プロジェクト サービスを使用してメッセージを記述する方法を示します、**出力**ウィンドウと**エラー一覧**単純なプロジェクト項目の種類の定義 ウィンドウ。  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     プロジェクト項目の種類の定義の詳細については、次を参照してください。[する方法: SharePoint プロジェクト項目の種類を定義する](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)です。  
  
## <a name="retrieving-the-service-in-server-explorer-extensions"></a>サーバー エクスプ ローラー拡張機能でのサービスの取得  
 拡張機能に、 **SharePoint 接続**内のノード**サーバー エクスプ ローラー**を使用してプロジェクトのサービスにアクセスすることができます、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>オブジェクト。  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>サーバー エクスプ ローラー拡張機能でサービスを取得するには  
  
1.  取得、<xref:System.IServiceProvider>オブジェクトから、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>拡張機能内のオブジェクト。  
  
2.  使用して、<xref:System.IServiceProvider.GetService%2A>を要求するメソッド、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>オブジェクト。  
  
     次のコード例は、プロジェクト サービスを使用してメッセージを記述する方法を示します、**出力**ウィンドウと**エラー一覧**リストのノードに、拡張機能を追加するショートカットメニューからウィンドウ**サーバー エクスプ ローラー**です。  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     拡張の詳細については、 **SharePoint 接続**内のノード**サーバー エクスプ ローラー**を参照してください[する方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)です。  
  
## <a name="retrieving-the-service-in-other-visual-studio-extensions"></a>その他の Visual Studio 拡張機能のサービスの取得  
 VSPackage、またはのどの Visual Studio 拡張機能にアクセスできるプロジェクト サービスを取得することができます、<xref:EnvDTE80.DTE2>を実装しているプロジェクト テンプレートのウィザードなど、オートメーション オブジェクト モデル内のオブジェクト、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>インターフェイスです。  
  
 要求することができます、VSPackage で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>次のメソッドのいずれかを使用してオブジェクト。  
  
-   <xref:System.IServiceProvider.GetService%2A>から派生するマネージ VSPackage のメソッド、<xref:Microsoft.VisualStudio.Shell.Package>クラスです。 詳細については、次を参照してください。[する方法: サービスを取得](../extensibility/how-to-get-a-service.md)です。  
  
-   静的な<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>メソッドです。 詳細については、次を参照してください。[使用 GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice)です。  
  
 アクセス権を持つ Visual Studio 拡張機能で、<xref:EnvDTE80.DTE2>オブジェクトを要求できます、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>オブジェクトを使用して、<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>のメソッド、<xref:Microsoft.VisualStudio.Shell.ServiceProvider>オブジェクト。 詳細については、次を参照してください。 [DTE オブジェクトからサービスを取得する](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object)です。  
  
## <a name="see-also"></a>参照  
 [SharePoint プロジェクト サービスの使用](../sharepoint/using-the-sharepoint-project-service.md)   
 [方法: サービスを取得](../extensibility/how-to-get-a-service.md)   
 [方法: プロジェクト テンプレートでウィザードを使用する](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
  