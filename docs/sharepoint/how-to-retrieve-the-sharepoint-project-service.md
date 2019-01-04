---
title: '方法: SharePoint プロジェクト サービスの取得 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dfd18de91848c8aabbdabc91fd37763418bb938a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891603"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>方法: SharePoint プロジェクト サービスを取得します。
  次の種類のソリューションで SharePoint プロジェクト サービスにアクセスすることができます。  
  
-   プロジェクトの拡張機能、プロジェクト項目の拡張機能、またはプロジェクト項目の種類の定義など、SharePoint プロジェクト システムの拡張機能。 これらの種類の拡張機能の詳細については、次を参照してください。 [SharePoint プロジェクト システムを拡張](../sharepoint/extending-the-sharepoint-project-system.md)します。  
  
-   拡張機能、 **SharePoint 接続**ノード**サーバー エクスプ ローラー**します。 これらの種類の拡張機能の詳細については、次を参照してください。[サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)します。  
  
-   Visual Studio 拡張機能、VSPackage などの別の型。  
  
## <a name="retrieve-the-service-in-project-system-extensions"></a>プロジェクト システムの拡張機能でサービスを取得します。  
 SharePoint プロジェクト システムの拡張機能を使用してプロジェクトのサービスにアクセスすることができます、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>オブジェクト。  
  
 次の手順を使用して、プロジェクト サービスを取得することもできます。  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>プロジェクトの拡張機能でサービスを取得するには  
  
1.  実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>を探し、インターフェイス、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>メソッド。  
  
2.  使用して、 *projectService*サービスにアクセスするパラメーター。  
  
     次のコード例は、プロジェクト サービスを使用してメッセージを記述する方法を示します、**出力**ウィンドウと**エラー一覧**単純なプロジェクトの拡張機能ウィンドウ。  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     プロジェクトの拡張機能の作成の詳細については、次を参照してください。[方法。SharePoint プロジェクト拡張機能作成](../sharepoint/how-to-create-a-sharepoint-project-extension.md)です。  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>プロジェクト項目の拡張機能でサービスを取得するには  
  
1.  実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>を探し、インターフェイス、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>メソッド。  
  
2.  使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A>のプロパティ、 *projectItemType*パラメーターは、サービスを取得します。  
  
     次のコード例は、プロジェクト サービスを使用してメッセージを記述する方法を示します、**出力**ウィンドウと**エラー一覧**の単純な拡張機能にウィンドウ、**リスト定義**プロジェクト アイテム。  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     項目の拡張機能プロジェクトを作成する方法の詳細については、次を参照してください。[方法。SharePoint プロジェクト項目の拡張機能作成](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)です。  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>プロジェクト項目の種類の定義でサービスを取得するには  
  
1.  実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>を探し、インターフェイス、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>メソッド。  
  
2.  使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A>のプロパティ、 *typeDefinition*パラメーターは、サービスを取得します。  
  
     次のコード例は、プロジェクト サービスを使用してメッセージを記述する方法を示します、**出力**ウィンドウと**エラー一覧**単純なプロジェクト項目の種類定義のウィンドウ。  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     プロジェクト項目の種類の定義の詳細については、次を参照してください。[方法。SharePoint プロジェクト項目の種類定義](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)します。  
  
## <a name="retrieve-the-service-in-server-explorer-extensions"></a>サーバー エクスプ ローラー拡張機能でサービスを取得します。  
 拡張機能で、 **SharePoint 接続**ノード**サーバー エクスプ ローラー**、プロジェクト サービスを使用してアクセスすることができます、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>オブジェクト。  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>サーバー エクスプ ローラー拡張機能でサービスを取得するには  
  
1.  取得、<xref:System.IServiceProvider>オブジェクトから、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>拡張機能内のオブジェクト。  
  
2.  使用して、<xref:System.IServiceProvider.GetService%2A>を要求するメソッド、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>オブジェクト。  
  
     次のコード例は、プロジェクト サービスを使用してメッセージを記述する方法を示します、**出力**ウィンドウと**エラー一覧**内のノードの一覧に、拡張機能を追加するショートカットメニューからウィンドウ**サーバー エクスプ ローラー**します。  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     拡張の詳細については、 **SharePoint 接続**ノード**サーバー エクスプ ローラー**を参照してください[方法。サーバー エクスプ ローラーでの SharePoint ノードを拡張](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)します。  
  
## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>その他の Visual Studio 拡張機能でサービスを取得します。  
 VSPackage、または Visual Studio の拡張機能にアクセスできるプロジェクト サービスを取得することができます、 <xref:EnvDTE80.DTE2> 、オートメーション オブジェクト モデルを実装するプロジェクト テンプレートのウィザードなどのオブジェクト、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>インターフェイス。  
  
 要求することができます、VSPackage で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>次のメソッドのいずれかを使用してオブジェクト。  
  
- <xref:System.IServiceProvider.GetService%2A>から派生したマネージ VSPackage のメソッド、<xref:Microsoft.VisualStudio.Shell.Package>クラス。 詳細については、「[方法 :サービスを取得](../extensibility/how-to-get-a-service.md)します。  
  
- 静的な<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>メソッド。 詳細については、次を参照してください。[使用 GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice)します。  
  
  Visual Studio の拡張機能にアクセスできる、<xref:EnvDTE80.DTE2>オブジェクトを要求できます、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>オブジェクトを使用して、<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>のメソッドを<xref:Microsoft.VisualStudio.Shell.ServiceProvider>オブジェクト。 詳細については、次を参照してください。 [DTE オブジェクトからサービスを取得する](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクト サービスを使用します。](../sharepoint/using-the-sharepoint-project-service.md)   
 [方法: サービスを取得します。](../extensibility/how-to-get-a-service.md)   
 [方法: プロジェクト テンプレートにウィザードの使用](../extensibility/how-to-use-wizards-with-project-templates.md)  
