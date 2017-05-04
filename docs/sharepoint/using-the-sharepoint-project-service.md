---
title: "Using the SharePoint Project Service | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: bfb6cbc7-6c28-4e1a-abb4-88f149e7712c
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Using the SharePoint Project Service
  SharePoint プロジェクト システムには、そのプロジェクト システムに関係するタスクを実行するために使用できるプロジェクト サービスが含まれています。  プロジェクト サービスは <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> オブジェクトです。  
  
 SharePoint プロジェクト サービスは、SharePoint ツールのどの拡張機能からでもアクセスできます。  また、アドインや VSPackage など、他の種類の Visual Studio 拡張機能の中でもアクセスできます。  詳細については、「[How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)」を参照してください。  
  
## プロジェクト サービスの機能  
 次の表に、SharePoint プロジェクト サービスを使用して実行できるタスクと、各タスクを実行するために使用する <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> メソッドまたはプロパティの一覧を示します。  
  
|タスク|使用するメンバー|  
|---------|--------------|  
|Visual Studio で開いている SharePoint プロジェクトにアクセスする。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> プロパティ。|  
|使用可能なすべての種類の SharePoint プロジェクト項目にアクセスする \(組み込みプロジェクト項目の種類とカスタム プロジェクト項目の種類を含む\)。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> プロパティ。|  
|SharePoint プロジェクトで使用可能なすべての配置手順にアクセスする \(組み込み配置手順とカスタム配置手順を含む\)。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> プロパティ。|  
|SharePoint プロジェクトのコードを開発者がリファクタリングしたときに発生するイベントにアクセスする。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> プロパティ。|  
|SharePoint サーバー オブジェクト モデルを呼び出すカスタム *SharePoint コマンド*を実行する。  SharePoint コマンドの詳細については、「[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)」を参照してください。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> プロパティ。|  
|SharePoint プロジェクト システム内の種類を、Visual Studio オートメーション オブジェクト モデルまたは統合オブジェクト モデル内の種類に変換する \(あるいは逆方向に変換する\)。  詳細については、「[Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)」を参照してください。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> メソッド|  
|Visual Studioの **\[出力\]** ウィンドウまたは **\[エラー一覧\]** ウィンドウにメッセージを書き込む。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> プロパティ。|  
|Visual Studio で使用可能な他のサービスにアクセスする。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> プロパティ。|  
|ソリューションのデバッグに使用するローカル SharePoint サイトのインストール フォルダーのパスを取得する。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> プロパティ。|  
|[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] と [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] のどちらがコンピューターにインストールされているかを判別する。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> プロパティ。|  
|SharePoint ソリューションの機能またはパッケージを検証する。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> プロパティ。|  
  
## 参照  
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [方法: DTE オブジェクトからサービスを取得する](http://msdn.microsoft.com/library/bb166401.aspx)  
  
  