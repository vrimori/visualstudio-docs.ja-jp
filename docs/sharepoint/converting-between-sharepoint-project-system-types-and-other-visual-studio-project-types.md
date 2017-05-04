---
title: "Converting Between SharePoint Project System Types and Other Visual Studio Project Types | Microsoft Docs"
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
ms.assetid: ad5d8ab2-1659-4e6a-8783-47e0dad44b11
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Converting Between SharePoint Project System Types and Other Visual Studio Project Types
  SharePoint プロジェクト システムのオブジェクトがあるとき、Visual Studio オートメーション オブジェクト モデルまたは統合オブジェクト モデルの対応するオブジェクトの機能が必要になる場合があります \(またその逆もあります\)。  このような場合は、SharePoint プロジェクト サービスの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> メソッドを使用して、オブジェクトを別のオブジェクト モデルに変換できます。  
  
 たとえば、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> オブジェクトは存在していても、<xref:EnvDTE.Project> オブジェクトまたは <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> オブジェクトでしか使用できないメソッドが必要になる場合があります。  このような場合は、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> メソッドを使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> を <xref:EnvDTE.Project> または <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> に変換できます。  
  
 Visual Studio のオートメーション オブジェクト モデルと Visual Studio の統合オブジェクト モデルの詳細については、「[Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)」を参照してください。  
  
## 変換の型  
 次の表は、このメソッドを使用して SharePoint プロジェクト システムと他の Visual Studio オブジェクト モデルの間で変換できる型の一覧です。  
  
|SharePoint プロジェクト システムの型|対応するオートメーション\/統合オブジェクト モデルの型|  
|------------------------------|----------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> または<br /><br /> プロジェクトの基になる COM オブジェクトによって実装されている Visual Studio の統合オブジェクト モデル内の任意のインターフェイス。  このようなインターフェイスとしては、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> \(または、派生インターフェイス\)、および <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> があります。  プロジェクトによって実装される主要なインターフェイスのリストについては、「[プロジェクト モデルのコア コンポーネント](../extensibility/internals/project-model-core-components.md)」を参照してください。|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> または<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> のプロジェクト メンバーを識別する <xref:System.UInt32> 値 \(VSITEMID\)。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> のいくつかのメソッドは、この値を *itemid* パラメーターとして受け取ることができます。|  
  
## 例  
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> メソッドを使用して <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> オブジェクトを <xref:EnvDTE.Project> に変換する方法を次のコード例に示します。  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#2)]  
  
 この例には、次の項目が必要です。  
  
-   EnvDTE.dll アセンブリへの参照が含まれている SharePoint プロジェクト システムの拡張機能。  詳細については、「[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)」を参照してください。  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> イベントを処理する `projectService_ProjectAdded` メソッドを登録するコード  例については、「[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)」を参照してください。  
  
## 参照  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  