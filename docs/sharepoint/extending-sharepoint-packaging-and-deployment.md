---
title: "SharePoint のパッケージ化と配置を拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 4789ebb2-12bc-42b9-9427-e63d77137765
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d2239a73b5a6f35a3571af90f8bd2814150da9d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="extending-sharepoint-packaging-and-deployment"></a>SharePoint のパッケージ化と配置の拡張
  SharePoint プロジェクトのパッケージ化と配置のプロセスを拡張できます。
  
##  <a name="creating-deployment-steps"></a>配置手順を作成する  
 SharePoint プロジェクトを配置するとき、[!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] によって一連の配置手順が実行されます。 Visual Studio には、ソリューションの取り消しや追加など、さまざまなタスクに関する組み込みの配置手順が用意されています。 ただし、配置手順は独自に作成することもできます。  
  
 配置手順を作成する方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: SharePoint プロジェクトのカスタム配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)です。  
  
##  <a name="creating-deployment-configurations"></a>配置構成を作成する  
 配置構成は、特定のプロジェクトについて実行される一連の配置手順ですが、すべての SharePoint プロジェクト項目に影響を与えることがあります。 すべての配置構成には、プロジェクトが配置されるときに実行される手順と、プロジェクトが取り消されるときに実行される手順が含まれています。 [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)]2 つの組み込みの配置構成が含まれていますが、独自に作成することもできます。 配置構成を自分で作成する場合、組み込みの配置手順と独自に作成した配置手順とを混在させることができます。  
  
 配置構成を作成する方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: SharePoint プロジェクトのカスタム配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)です。  
  
##  <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>SharePoint ソリューションの配置時または取り消し時にコードを実行する  
 SharePoint ソリューションの配置時または取り消し時に、別途タスクを実行するためにイベントを処理することができます。 Visual Studio では、次のシナリオで処理できるイベントが生成されます。  
  
-   SharePoint プロジェクト項目について各配置手順が実行される前後。 詳細については、次を参照してください。[する方法: 実行時に配置手順のコードが実行される](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)です。  
  
-   SharePoint プロジェクトの配置または取り消しが行われる前後。 詳細については、次を参照してください。[する方法: 実行コードと、SharePoint プロジェクトの配置または取り消し時](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)です。  
  
##  <a name="handling-deployment-conflicts"></a>配置競合の処理  
 モジュール、Web パーツ、リスト インスタンス、コンテンツ タイプなど、一部の種類の SharePoint プロジェクト項目では、組み込みの配置競合の解決が用意されています。 これらのいずれかのプロジェクト項目が含まれるソリューションを配置すると、Visual Studio は、まず、配置しようとしている項目に含まれるファイルと同じ名前、URL、または ID を持つファイルが、SharePoint サイトに既に存在しているかどうかを確認します。 競合が発生する場合、Visual Studio に自動的に競合を解決させることも、Visual Studio に競合を解決させるか配置を取り消すかを判断するようユーザーに要求することもできます。 詳細については、次を参照してください。[トラブルシューティング SharePoint のパッケージ化と配置](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)です。  
  
 配置競合を確認および解決する独自のコードを使用して、この機能を拡張できます。 詳細については、次を参照してください。[する方法: 配置競合の処理](../sharepoint/how-to-handle-deployment-conflicts.md)です。  
  
##  <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>プロジェクトが配置される前と後にコマンド ライン操作を実行する  
 SharePoint ソリューションの配置時にコマンド ライン操作を実行する場合、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> プロパティと <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> プロパティを設定することができます。 これらのコマンドは、プロジェクトが配置される前と後に Visual Studio によって実行されます。  
  
 場合によっては、配置の競合が発生することがあります。 競合を解決する方法はいくつかあります。 詳細については、次を参照してください。[トラブルシューティング SharePoint のパッケージ化と配置](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)です。  
  
##  <a name="customizing-validation-rules"></a>検証規則のカスタマイズ  
 ソリューション パッケージ (.wsp) を配置する前に、フィーチャーまたはパッケージが有効であることを検証するために、カスタムのフィーチャー検証規則およびパッケージ検証規則を作成できます。 たとえば、検証に関する問題の修正に役立つように、情報、警告、またはエラーを開発者に報告できます。 詳細については、次を参照してください。[する方法: カスタム機能の作成と SharePoint ソリューションのパッケージ検証規則](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)です。  
  
## <a name="see-also"></a>参照  
 [方法: 実行時に配置手順のコードが実行されます](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [チュートリアル: SharePoint プロジェクトに対するカスタムの配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [方法: SharePoint ソリューションのカスタムのフィーチャーとパッケージ検証規則を作成します。](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [SharePoint プロジェクト システムの拡張](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
