---
title: SharePoint のパッケージ化と配置の拡張 |Microsoft Docs
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
ms.openlocfilehash: 8c6ca4b347cdd733ac166782d8e78dc8e78e0772
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325366"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>SharePoint のパッケージ化と配置を拡張します。
  SharePoint プロジェクトのパッケージ化と配置のプロセスを拡張できます。
  
## <a name="create-deployment-steps"></a>配置手順を作成します。
 SharePoint プロジェクトを配置するとき、[!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] によって一連の配置手順が実行されます。 Visual Studio には、ソリューションの取り消しや追加など、さまざまなタスクに関する組み込みの配置手順が用意されています。 ただし、配置手順は独自に作成することもできます。  
  
 配置手順を作成する方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: SharePoint プロジェクトのカスタム配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)です。  
  
## <a name="create-deployment-configurations"></a>展開構成を作成します。
 配置構成は、特定のプロジェクトについて実行される一連の配置手順ですが、すべての SharePoint プロジェクト項目に影響を与えることがあります。 すべての配置構成には、プロジェクトが配置されるときに実行される手順と、プロジェクトが取り消されるときに実行される手順が含まれています。 [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] 2 つの組み込みの配置構成が含まれますが、独自に作成することもできます。 配置構成を自分で作成する場合、組み込みの配置手順と独自に作成した配置手順とを混在させることができます。  
  
 配置構成を作成する方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: SharePoint プロジェクトのカスタム配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)です。  
  
## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>SharePoint ソリューションを配置または取り消すときに、コードを実行します。
 SharePoint ソリューションの配置時または取り消し時に、別途タスクを実行するためにイベントを処理することができます。 Visual Studio では、次のシナリオで処理できるイベントが生成されます。  
  
-   SharePoint プロジェクト項目について各配置手順が実行される前後。 詳細については、次を参照してください。[方法: 配置手順の実行時にコードを実行](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)します。  
  
-   SharePoint プロジェクトの配置または取り消しが行われる前後。 詳細については、次を参照してください。[方法: SharePoint プロジェクトを配置または取り消すときに、コードを実行](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)します。  
  
## <a name="handle-deployment-conflicts"></a>配置競合を処理します。
 モジュール、Web パーツ、リスト インスタンス、コンテンツ タイプなど、一部の種類の SharePoint プロジェクト項目では、組み込みの配置競合の解決が用意されています。 これらのいずれかのプロジェクト項目が含まれるソリューションを配置すると、Visual Studio は、まず、配置しようとしている項目に含まれるファイルと同じ名前、URL、または ID を持つファイルが、SharePoint サイトに既に存在しているかどうかを確認します。 競合が発生する場合、Visual Studio に自動的に競合を解決させることも、Visual Studio に競合を解決させるか配置を取り消すかを判断するようユーザーに要求することもできます。 詳細については、次を参照してください。 [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)します。  
  
 配置競合を確認および解決する独自のコードを使用して、この機能を拡張できます。 詳細については、次を参照してください。[方法: 配置競合を処理](../sharepoint/how-to-handle-deployment-conflicts.md)します。  
  
## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>前に、またはプロジェクトを配置後コマンドライン操作を実行します。
 SharePoint ソリューションの配置時にコマンド ライン操作を実行する場合、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> プロパティと <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> プロパティを設定することができます。 これらのコマンドは、プロジェクトが配置される前と後に Visual Studio によって実行されます。  
  
 場合によっては、配置の競合が発生することがあります。 競合を解決する方法はいくつかあります。 詳細については、次を参照してください。[のトラブルシューティングを行う SharePoint のパッケージ化と配置](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)します。  
  
## <a name="customize-validation-rules"></a>検証規則をカスタマイズします。
 ソリューション パッケージ (.wsp) を配置する前に、フィーチャーまたはパッケージが有効であることを検証するために、カスタムのフィーチャー検証規則およびパッケージ検証規則を作成できます。 たとえば、検証に関する問題の修正に役立つように、情報、警告、またはエラーを開発者に報告できます。 詳細については、次を参照してください。[方法: SharePoint ソリューションの検証規則を使用したカスタムのフィーチャーとパッケージの作成](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)です。  
  
## <a name="see-also"></a>関連項目
 [方法: 配置手順の実行時にコードを実行](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [チュートリアル: SharePoint プロジェクトのカスタム配置手順を作成します。](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [方法: SharePoint ソリューションの検証規則を使用したカスタムのフィーチャーとパッケージの作成](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [SharePoint プロジェクト システムを拡張します。](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
