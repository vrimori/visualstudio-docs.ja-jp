---
title: '方法: 配置競合の処理 |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d7c30a7c634c30c9fe3e92ef988d7d8fc043cf6b
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119867"
---
# <a name="how-to-handle-deployment-conflicts"></a>方法: 配置競合の処理
  SharePoint プロジェクト項目の配置の競合を処理するために、独自のコードを行うことができます。 たとえば、現在のプロジェクト アイテム内のファイルが、配置場所に既に存在し、現在のプロジェクト項目を展開する前に配置されたファイルを削除かどうかが判断する可能性があります。 配置競合の詳細については、次を参照してください。[拡張 SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)します。  
  
### <a name="to-handle-a-deployment-conflict"></a>配置の競合を処理するには  
  
1.  プロジェクト項目の拡張機能、プロジェクトの拡張機能、または新しいプロジェクト項目の種類の定義を作成します。 詳細については、次のトピックを参照してください。  
  
    -   [方法: SharePoint プロジェクト項目の拡張機能の作成](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [方法: SharePoint プロジェクト拡張機能の作成](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [方法: SharePoint プロジェクト項目の種類の定義](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  拡張機能、処理、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>のイベント、 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> (プロジェクト項目の拡張機能またはプロジェクトの拡張機能) 内のオブジェクトまたは<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>(新しいプロジェクト項目の種類の定義) 内のオブジェクト。  
  
3.  イベント ハンドラーで配置されているプロジェクト項目と、シナリオに適用される条件に基づいて、SharePoint サイトにデプロイ済みのソリューション間の競合があるかどうかを決定します。 使用することができます、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A>配置されているプロジェクト項目を分析するイベント引数のパラメーターのプロパティとは、この目的用に定義する SharePoint コマンドを呼び出すことによって展開場所にあるファイルを分析できます。  
  
     多くの種類の競合では、可能性があります最初を確認するどの展開手順を実行します。 使用してこれを行う、<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A>イベント引数のパラメーターのプロパティ。 通常は、組み込みの中に競合を検出しても意味が<xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution>配置の手順で確認できます競合のいずれかの展開手順の中にします。  
  
4.  競合が存在する場合は、使用、<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>のメソッド、<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A>新たに作成するイベント引数のプロパティ<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>オブジェクト。 このオブジェクトは、配置の競合を表します。 呼び出しで、<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>メソッドも、競合を解決するために呼び出されるメソッドを指定します。  
  
## <a name="example"></a>例  
 次のコード例では、リスト定義プロジェクト項目のためのプロジェクト項目の拡張機能の配置の競合を処理するための基本的なプロセスを示します。 さまざまな種類のプロジェクト項目の配置の競合を処理するために別の文字列を渡す、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>します。 詳細については、次を参照してください。[拡張の SharePoint プロジェクト アイテム](../sharepoint/extending-sharepoint-project-items.md)します。  
  
 わかりやすくするため、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>この例では、イベント ハンドラーでは、配置の競合が存在すると仮定 (これは、常に新しく追加<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>オブジェクト)、および`Resolve`メソッドは単に返します**true**ことを示します競合が解決されました。 実際のシナリオで、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>イベント ハンドラーが最初に現在のプロジェクト アイテム内のファイルと、デプロイ場所にあるファイルの間で競合が存在する場合を判断し、追加、<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>オブジェクトの競合が存在するかどうかのみです。 たとえば、使用する場合があります、`e.ProjectItem.Files`プロパティとプロジェクト アイテム内のファイルを分析するイベント ハンドラーでは、配置場所のファイルを分析するための SharePoint コマンドを呼び出すことができます。 同様に、実際のシナリオで、`Resolve`メソッドは、SharePoint サイト上の競合を解決するための SharePoint コマンドを呼び出すことができます。 SharePoint コマンドの作成に関する詳細については、次を参照してください。[方法: SharePoint コマンドを作成する](../sharepoint/how-to-create-a-sharepoint-command.md)します。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compile-the-code"></a>コードをコンパイルします  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>拡張機能をデプロイします。  
 拡張機能を展開するには、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint のパッケージ化と配置を拡張します。](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [SharePoint プロジェクト項目を拡張します。](../sharepoint/extending-sharepoint-project-items.md)   
 [方法: 配置手順の実行時にコードを実行](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [方法: SharePoint コマンドを作成します。](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
