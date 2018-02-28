---
title: "方法: 配置競合の処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: c3bbd5bc7d69fbc48d2c754151a3ec6b5fcb612c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-handle-deployment-conflicts"></a>方法: 配置競合を処理する
  SharePoint プロジェクト項目の展開の競合を処理するコードを提供できます。 たとえば、現在のプロジェクト アイテム内のファイルが配置場所に既に存在し、現在のプロジェクト項目を展開する前に配置されたファイルを削除するかどうかが判断する場合もあります。 配置競合の詳細については、次を参照してください。[を拡張する SharePoint のパッケージ化と配置](../sharepoint/extending-sharepoint-packaging-and-deployment.md)です。  
  
### <a name="to-handle-a-deployment-conflict"></a>配置の競合を処理するには  
  
1.  プロジェクト項目の拡張機能、プロジェクトの拡張機能、または新しいプロジェクト項目の種類の定義を作成します。 詳細については、次のトピックを参照してください。  
  
    -   [方法: SharePoint プロジェクト項目の拡張機能を作成する](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [方法: SharePoint プロジェクトの拡張機能を作成する](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [方法: SharePoint プロジェクト項目の種類を定義する](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  拡張機能、処理、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>のイベント、 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> (プロジェクト項目の拡張機能またはプロジェクトの拡張機能) 内のオブジェクトまたは<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>オブジェクト (新しいプロジェクト項目の種類の定義) です。  
  
3.  イベント ハンドラーでは、展開されているプロジェクト項目と自分のシナリオに適用される条件を基に、SharePoint サイトで、配置されたソリューション間の競合があるかどうかを決定します。 使用することができます、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A>して、展開されているプロジェクト アイテムを分析するイベントの引数パラメーターのプロパティは、この目的用に定義した SharePoint コマンドを呼び出すことによって配置場所のファイルを分析できます。  
  
     多くの種類の競合の可能性があります最初を確認するどの展開手順の実行中です。 使用してこれを行う、<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A>イベント引数のパラメーターのプロパティです。 組み込みの中に競合を検出すると効果的ですが<xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution>配置の手順で確認できます競合のいずれかの展開手順の中にします。  
  
4.  競合が存在する場合を使用して、<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>のメソッド、 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> 、新たに作成するのには、イベント引数のプロパティ<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>オブジェクト。 このオブジェクトは、配置の競合を表します。 呼び出しで、<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>メソッドも、競合を解決するために呼び出されるメソッドを指定します。  
  
## <a name="example"></a>例  
 次のコード例では、リスト定義プロジェクト項目用のプロジェクト項目の拡張機能の展開の競合を処理するための基本的なプロセスを示します。 さまざまな種類のプロジェクト項目の配置の競合を処理するために別の文字列を渡す、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>です。 詳細については、次を参照してください。 [SharePoint プロジェクト項目の拡張](../sharepoint/extending-sharepoint-project-items.md)です。  
  
 わかりやすくするため、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>この例ではイベント ハンドラーは、配置の競合が存在することを想定しています (つまり、常に追加、新しい<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>オブジェクト)、および`Resolve`メソッドだけを返します**true**ことを示す競合が解決されました。 実際のシナリオでは、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>イベント ハンドラーが最初に現在のプロジェクト アイテム内のファイルと配置場所でファイル間で競合が存在する場合を確認し、追加、<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>競合が存在するかどうかのオブジェクトのみです。 たとえば、使用する場合があります、`e.ProjectItem.Files`プロパティ、イベント ハンドラーをして、プロジェクト項目内のファイルを分析するには、配置場所のファイルを分析するための SharePoint コマンドを呼び出す可能性があります。 同様に、実際のシナリオで、`Resolve`メソッドは、SharePoint サイト上の競合を解決するための SharePoint コマンドを呼び出すことがあります。 SharePoint コマンドの作成に関する詳細については、次を参照してください。[する方法: SharePoint コマンドを作成する](../sharepoint/how-to-create-a-sharepoint-command.md)です。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>拡張機能の配置  
 拡張機能を展開するには、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>参照  
 [SharePoint の拡張のパッケージ化と配置](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [SharePoint プロジェクト項目の拡張](../sharepoint/extending-sharepoint-project-items.md)   
 [方法: 実行時に配置手順のコードが実行されます](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [方法: SharePoint コマンドを作成する](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  