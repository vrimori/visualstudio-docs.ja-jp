---
title: SharePoint プロジェクト サービスの使用 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 90df435e2c6c20b43d12169b32780eefc22c1d70
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871547"
---
# <a name="use-the-sharepoint-project-service"></a>SharePoint プロジェクト サービスを使用します。
  SharePoint プロジェクト システムには、そのプロジェクト システムに関係するタスクを実行するために使用できるプロジェクト サービスが含まれています。 プロジェクト サービスは <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> オブジェクトです。  
  
 SharePoint プロジェクト サービスは、SharePoint ツールのどの拡張機能からでもアクセスできます。 また、アドインや VSPackage など、他の種類の Visual Studio 拡張機能の中でもアクセスできます。 詳細については、「[方法 :SharePoint プロジェクト サービスを取得](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)します。  
  
## <a name="project-service-features"></a>プロジェクト サービスの機能
 次の表に、SharePoint プロジェクト サービスを使用して実行できるタスクと、各タスクを実行するために使用する <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> メソッドまたはプロパティの一覧を示します。  
  
|タスク|使用するメンバー|  
|----------|-------------------|  
|Visual Studio で開いている SharePoint プロジェクトにアクセスする。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> プロパティ。|  
|使用可能なすべての種類の SharePoint プロジェクト項目にアクセスする (組み込みプロジェクト項目の種類とカスタム プロジェクト項目の種類を含む)。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> プロパティ。|  
|SharePoint プロジェクトで使用可能なすべての配置手順にアクセスする (組み込み配置手順とカスタム配置手順を含む)。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> プロパティ。|  
|SharePoint プロジェクトのコードを開発者がリファクタリングしたときに発生するイベントにアクセスする。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> プロパティ。|  
|カスタム実行*SharePoint コマンド*を SharePoint サーバー オブジェクト モデルを呼び出します。 SharePoint コマンドの詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)します。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> プロパティ。|  
|SharePoint プロジェクト システム内の種類を、Visual Studio オートメーション オブジェクト モデルまたは統合オブジェクト モデル内の種類に変換する (あるいは逆方向に変換する)。 詳細については、次を参照してください。 [SharePoint プロジェクト システムの種類とその他の Visual Studio プロジェクトの種類間で変換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)します。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> メソッド|  
|メッセージ ログを書き込む、**出力**ウィンドウまたは**エラー一覧**Visual Studio のウィンドウ。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> プロパティ。|  
|Visual Studio で使用可能な他のサービスにアクセスする。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> プロパティ。|  
|ソリューションのデバッグに使用するローカル SharePoint サイトのインストール フォルダーのパスを取得する。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> プロパティ。|  
|[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] と [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] のどちらがコンピューターにインストールされているかを判別する。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> プロパティ。|  
|SharePoint ソリューションの機能またはパッケージを検証する。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> プロパティ。|  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクト システムの種類とその他の Visual Studio プロジェクトの種類間の変換します。](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [方法: SharePoint プロジェクト サービスを取得します。](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Visual Studio の SharePoint ツールを拡張します。](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [ツールの拡張機能を SharePoint のプログラミング モデルの概要](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [方法: DTE オブジェクトからサービスを取得します。](https://msdn.microsoft.com/library/bb166401.aspx)  
