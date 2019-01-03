---
title: '方法: 実行コードと SharePoint プロジェクトの配置時または取り消し時 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bb5ba251df3271e704ea4b455c5cc47003ab8e2e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933623"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>方法: SharePoint プロジェクトを配置または取り消すときに、コードを実行します。
  SharePoint プロジェクトを配置または取り消すときに、追加のタスクを実行する場合は、Visual Studio によって生成されるイベントを処理できます。 詳細については、次を参照してください。 [SharePoint の拡張のパッケージ化と配置](../sharepoint/extending-sharepoint-packaging-and-deployment.md)します。  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>SharePoint プロジェクトのコードを実行するには、配置時または取り消し  
  
1. プロジェクト項目の拡張機能、プロジェクトの拡張機能、または新しいプロジェクト項目の種類の定義を作成します。 詳細については、次のトピックを参照してください。  
  
   -   [方法: SharePoint プロジェクト項目の拡張機能を作成します。](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
   -   [方法: SharePoint プロジェクト拡張機能を作成します。](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
   -   [方法: SharePoint プロジェクト項目の種類を定義します。](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2. 拡張機能のアクセス、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>オブジェクト。 詳細については、「[方法 :SharePoint プロジェクト サービスを取得](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)します。  
  
3. 処理、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted>プロジェクト サービスのイベント。  
  
4. イベント ハンドラーを使用して、<xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs>パラメーターの現在の配置セッションに関する情報を取得します。 たとえば、どのプロジェクトが現在の配置セッションとされているかどうかを判断できます配置または取り消します。  
  
   次のコード例は、処理する方法を示します、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted>プロジェクトの拡張機能内のイベント。 この拡張機能を追加のメッセージを書き込みます、**出力**デプロイが開始し、SharePoint プロジェクトの完了時にウィンドウ。  
  
   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>拡張機能をデプロイします。  
 拡張機能を展開するには、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint のパッケージ化と配置を拡張します。](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [方法: 配置手順の実行時にコードを実行します。](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
