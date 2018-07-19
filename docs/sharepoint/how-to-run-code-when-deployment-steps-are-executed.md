---
title: '方法: 実行コードと配置手順の実行 |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: cebd88cc49afa1092dfcd1d67ffdbf0fa3567ad0
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119767"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>方法: 配置手順の実行時にコードを実行
  SharePoint プロジェクトの配置手順の追加のタスクを実行する場合は、前に、SharePoint プロジェクト アイテムと Visual Studio が各デプロイの手順を実行後に発生するイベントを処理できます。 詳細については、次を参照してください。[拡張 SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)します。  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>配置手順の実行時にコードを実行するには  
  
1.  プロジェクト項目の拡張機能、プロジェクトの拡張機能、または新しいプロジェクト項目の種類の定義を作成します。 詳細については、次のトピックを参照してください。  
  
    -   [方法: SharePoint プロジェクト項目の拡張機能の作成](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [方法: SharePoint プロジェクト拡張機能の作成](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [方法: SharePoint プロジェクト項目の種類の定義](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  拡張機能、処理、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted>のイベント、 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> (プロジェクト項目の拡張機能またはプロジェクトの拡張機能) 内のオブジェクトまたは<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>(新しいプロジェクト項目の種類の定義) 内のオブジェクト。  
  
3.  イベント ハンドラーを使用して、<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs>と<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs>パラメーター配置手順に関する情報を取得します。 たとえば、どの展開手順を実行して、ソリューションがされているかどうかを判断できます配置または取り消します。  
  
## <a name="example"></a>例  
 次のコード例は、処理する方法を示します、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted>リスト インスタンスのプロジェクト項目の拡張機能内のイベント。 この拡張機能を追加のメッセージを書き込みます、**出力**ウィンドウを展開して、ソリューションの取り消し中に、Visual Studio でアプリケーション プールがリサイクルされる場合。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compile-the-code"></a>コードをコンパイルします  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>拡張機能をデプロイします。  
 拡張機能を展開するには、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint のパッケージ化と配置を拡張します。](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [チュートリアル: SharePoint プロジェクトのカスタム配置手順を作成します。](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [方法: SharePoint プロジェクトを配置または取り消すときに、コードを実行](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  
