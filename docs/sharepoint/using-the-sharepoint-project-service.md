---
title: SharePoint プロジェクト サービスの使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: efe2e2073ead64bfbc697b9d6c824066af947580
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-sharepoint-project-service"></a>SharePoint プロジェクト サービスの使用
  SharePoint プロジェクト システムには、そのプロジェクト システムに関係するタスクを実行するために使用できるプロジェクト サービスが含まれています。 プロジェクト サービスは <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> オブジェクトです。  
  
 SharePoint プロジェクト サービスは、SharePoint ツールのどの拡張機能からでもアクセスできます。 また、アドインや VSPackage など、他の種類の Visual Studio 拡張機能の中でもアクセスできます。 詳細については、次を参照してください。[する方法: SharePoint プロジェクト サービスを取得](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)です。  
  
## <a name="project-service-features"></a>プロジェクト サービスの機能  
 次の表に、SharePoint プロジェクト サービスを使用して実行できるタスクと、各タスクを実行するために使用する <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> メソッドまたはプロパティの一覧を示します。  
  
|タスク|使用するメンバー|  
|----------|-------------------|  
|Visual Studio で開いている SharePoint プロジェクトにアクセスする。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> プロパティ。|  
|使用可能なすべての種類の SharePoint プロジェクト項目にアクセスする (組み込みプロジェクト項目の種類とカスタム プロジェクト項目の種類を含む)。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> プロパティ。|  
|SharePoint プロジェクトで使用可能なすべての配置手順にアクセスする (組み込み配置手順とカスタム配置手順を含む)。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> プロパティ。|  
|SharePoint プロジェクトのコードを開発者がリファクタリングしたときに発生するイベントにアクセスする。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> プロパティ。|  
|カスタムの実行*SharePoint コマンド*SharePoint サーバー オブジェクト モデルを呼び出すことです。 SharePoint コマンドの詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)です。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> プロパティ。|  
|SharePoint プロジェクト システム内の種類を、Visual Studio オートメーション オブジェクト モデルまたは統合オブジェクト モデル内の種類に変換する (あるいは逆方向に変換する)。 詳細については、次を参照してください。[間で SharePoint プロジェクト システムの種類の変換およびその他の Visual Studio プロジェクトの種類](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)です。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> メソッド|  
|メッセージを書き込む、**出力**ウィンドウまたは**エラー一覧**Visual Studio のウィンドウ。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> プロパティ。|  
|Visual Studio で使用可能な他のサービスにアクセスする。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> プロパティ。|  
|ソリューションのデバッグに使用するローカル SharePoint サイトのインストール フォルダーのパスを取得する。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> プロパティ。|  
|[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] と [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] のどちらがコンピューターにインストールされているかを判別する。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> プロパティ。|  
|SharePoint ソリューションの機能またはパッケージを検証する。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> プロパティ。|  
  
## <a name="see-also"></a>関連項目  
 [SharePoint プロジェクト システムの種類とその他の Visual Studio プロジェクトの種類間の変換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [方法: SharePoint プロジェクト サービスの取得](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Visual Studio での SharePoint ツールを拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [ツールの拡張機能を SharePoint のプログラミング モデルの概要](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [方法: DTE オブジェクトからサービスを取得する](http://msdn.microsoft.com/library/bb166401.aspx)  
  
  