---
title: "How to: Retrieve the SharePoint Project Service | Microsoft Docs"
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
  - "SharePoint project service"
ms.assetid: 3d8b7adf-2603-4247-9b61-6326a1dd0dec
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# How to: Retrieve the SharePoint Project Service
  SharePoint プロジェクト サービスには、次の種類のソリューションからアクセスできます。  
  
-   SharePoint プロジェクト システムの拡張機能 \(プロジェクトの拡張機能、プロジェクト項目の拡張機能、プロジェクト項目の種類の定義など\)。  これらの拡張機能の種類の詳細については、「[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)」を参照してください。  
  
-   **サーバー エクスプローラー**の **\[SharePoint 接続\]** ノードの拡張  これらの拡張機能の種類の詳細については、「[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)」を参照してください。  
  
-   その他の種類の Visual Studio 拡張機能 \(アドイン、VSPackage など\)  
  
## プロジェクト システムの拡張機能でのサービスの取得  
 SharePoint プロジェクト システムの拡張機能からプロジェクト サービスにアクセスするには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> プロパティを使用します。  
  
 また、プロジェクト サービスは、次の手順に従って取得することもできます。  
  
#### プロジェクトの拡張機能でサービスを取得するには  
  
1.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> インターフェイスの実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> メソッドを探します。  
  
2.  サービスにアクセスするには、*projectService* パラメーターを使用します。  
  
     次のコード例は、プロジェクト サービスを使用して、単純なプロジェクト拡張機能でメッセージを **\[出力\]** ウィンドウおよび **\[エラー一覧\]** ウィンドウに書き込む方法を示します。  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#1)]  
  
     プロジェクトの拡張機能の作成の詳細については、「[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)」を参照してください。  
  
#### プロジェクト項目の拡張機能でサービスを取得するには  
  
1.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> インターフェイスの実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> メソッドを探します。  
  
2.  サービスを取得するには、*projectItemType* パラメーターの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> プロパティを使用します。  
  
     次のコード例は、プロジェクト サービスを使用して、**リスト定義**プロジェクト項目の単純な拡張機能でメッセージを **\[出力\]** ウィンドウおよび **\[エラー一覧\]** ウィンドウに書き込む方法を示します。  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#2)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#2)]  
  
     プロジェクト項目の拡張機能の作成の詳細については、「[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)」を参照してください。  
  
#### プロジェクト項目の種類の定義でサービスを取得するには  
  
1.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> インターフェイスの実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> メソッドを探します。  
  
2.  サービスを取得するには、*typeDefinition* パラメーターの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> プロパティを使用します。  
  
     次のコード例は、プロジェクト サービスを使用して、単純なプロジェクト項目の種類の定義でメッセージを **\[出力\]** ウィンドウおよび **\[エラー一覧\]** ウィンドウに書き込む方法を示します。  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#3)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#3)]  
  
     プロジェクト項目の種類の詳細については、「[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)」を参照してください。  
  
## サーバー エクスプローラーの拡張機能でのサービスの取得  
 **サーバー エクスプローラー**の **\[SharePoint 接続\]** ノードの拡張機能からプロジェクト サービスにアクセスするには、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> プロパティを使用します。  
  
#### サーバー エクスプローラーの拡張機能でサービスを取得するには  
  
1.  拡張機能の <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> プロパティから <xref:System.IServiceProvider> オブジェクトを取得します。  
  
2.  <xref:System.IServiceProvider.GetService%2A> メソッドを使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> オブジェクトを要求します。  
  
     次のコード例は、プロジェクト サービスを使用して、拡張機能によって**サーバー エクスプローラー**のリストのノードに追加されるショートカット メニューでメッセージを **\[出力\]** ウィンドウおよび **\[エラー一覧\]** ウィンドウに書き込む方法を示します。  
  
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/vb/extension/extension.vb#1)]  
  
     **サーバー エクスプローラー**の **\[SharePoint 接続\]** ノードの拡張の詳細については、「[How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)」を参照してください。  
  
## 他の Visual Studio 拡張機能でのサービスの取得  
 VSPackage で、またはオートメーション オブジェクト モデル \(アドイン、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスを実装するプロジェクト テンプレート ウィザードなど\) の <xref:EnvDTE80.DTE2> オブジェクトにアクセスできる Visual Studio 拡張機能で、プロジェクト サービスを取得できます。  
  
 VSPackage で <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> オブジェクトを要求するには、次のいずれかのメソッドを使用します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Package> クラスから派生するマネージ VSPackage の <xref:System.IServiceProvider.GetService%2A> メソッド  詳細については、「[方法: サービスを取得](../Topic/How%20to:%20Get%20a%20Service.md)」を参照してください。  
  
-   静的な <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> メソッド  詳細については、「[方法: GetGlobalService を使用する](../Topic/How%20to:%20Use%20GetGlobalService.md)」を参照してください。  
  
 <xref:EnvDTE80.DTE2> オブジェクトにアクセスできる Visual Studio 拡張機能で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> オブジェクトを要求するには、<xref:Microsoft.VisualStudio.Shell.ServiceProvider> オブジェクトの <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> メソッドを使用します。  詳細については、「[方法: DTE オブジェクトからサービスを取得する](../Topic/How%20to:%20Get%20a%20Service%20from%20the%20DTE%20Object.md)」を参照してください。  
  
### 例  
 Visual Studio アドインで、プロジェクト サービスを取得する方法を次のコード例に示します。  このコード例を使用するには、アドイン プロジェクトの `Connect` クラスから実行します。  `_applicationObject` オブジェクトがアドイン プロジェクトで自動的に生成されます。このオブジェクトは、<xref:EnvDTE80.DTE2> インターフェイスのインスタンスです。  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#1)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#1)]  
  
 この例には、次の項目が必要です。  
  
-   Visual Studio アドイン プロジェクト  詳細については、「[How to: Create an Add-In](../Topic/How%20to:%20Create%20an%20Add-In.md)」を参照してください。  
  
-   References to the Microsoft.VisualStudio.OLE.Interop, Microsoft.VisualStudio.Shell アセンブリおよび Microsoft.VisualStudio.SharePoint アセンブリへの参照  
  
## 参照  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [How to: Create an Add-In](../Topic/How%20to:%20Create%20an%20Add-In.md)   
 [方法: サービスを取得](../Topic/How%20to:%20Get%20a%20Service.md)   
 [方法: DTE オブジェクトからサービスを取得する](../Topic/How%20to:%20Get%20a%20Service%20from%20the%20DTE%20Object.md)   
 [方法 : プロジェクト テンプレートを組み合わせたウィザードを使用する](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)  
  
  