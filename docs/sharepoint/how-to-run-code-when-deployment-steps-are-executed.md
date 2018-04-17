---
title: '方法: 実行時に配置手順のコードが実行される |Microsoft ドキュメント'
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
ms.openlocfilehash: 1e678ac17ac2bdae2b92e34a91da41399c873a51
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>方法: 配置手順の実行時にコードを実行する
  SharePoint プロジェクトの配置手順の追加のタスクを実行する場合と後、Visual Studio が各展開の手順を実行する前に、SharePoint プロジェクト項目で発生するイベントを処理することができます。 詳細については、次を参照してください。[を拡張する SharePoint のパッケージ化と配置](../sharepoint/extending-sharepoint-packaging-and-deployment.md)です。  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>展開の手順を実行すると、コードを実行するには  
  
1.  プロジェクト項目の拡張機能、プロジェクトの拡張機能、または新しいプロジェクト項目の種類の定義を作成します。 詳細については、次のトピックを参照してください。  
  
    -   [方法: SharePoint プロジェクト項目の拡張機能を作成する](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [方法: SharePoint プロジェクトの拡張機能を作成する](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [方法: SharePoint プロジェクト項目の種類を定義する](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  拡張機能、処理、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted>のイベント、 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> (プロジェクト項目の拡張機能またはプロジェクトの拡張機能) 内のオブジェクトまたは<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>オブジェクト (新しいプロジェクト項目の種類の定義) です。  
  
3.  イベントのハンドラーを使用して、<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs>と<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs>パラメーター配置手順に関する情報を取得します。 どの展開手順を実行して、ソリューションがされているかどうかを決定するなど、配置時または取り消しできます。  
  
## <a name="example"></a>例  
 次のコード例は、処理する方法を示します、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted>リスト インスタンス プロジェクト項目の拡張機能内のイベントです。 この拡張機能に追加のメッセージを書き込みます、**出力**Visual Studio では、展開して、ソリューションの取り消し中に、アプリケーション プールがリサイクルされるときにウィンドウです。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>拡張機能の配置  
 拡張機能を展開するには、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint の拡張のパッケージ化と配置](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [チュートリアル: SharePoint プロジェクトに対するカスタムの配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [方法: SharePoint プロジェクトの配置時または取り消し時にコードを実行する](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  