---
title: '方法: サーバー エクスプ ローラーで、組み込みの SharePoint ノードのデータを取得 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ef3377b7c90aac183c1fc624743ea2882685eb27
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870364"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>方法: サーバー エクスプ ローラーで、組み込みの SharePoint ノードのデータを取得します。
  内の各組み込み SharePoint ノードの**サーバー エクスプ ローラー**ノードが表す基になる SharePoint コンポーネントのデータを取得できます。 詳細については、次を参照してください。[サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)します。  
  
## <a name="example"></a>例  
 次のコード例は、[リスト] ノードを表す基になる SharePoint リストのデータを取得する方法を示します**サーバー エクスプ ローラー**します。 既定では、一覧のノードにある、**ブラウザーで表示**コンテキスト メニュー項目を Web ブラウザーで、リストを開く をクリックしたことができます。 この例では、一覧のノードを拡張を追加して、 **Visual Studio でのビュー**リストを Visual Studio で直接表示されるコンテキスト メニュー項目。 コードでは、Visual Studio で開きますリストの URL を取得するノードのリストのデータにアクセスします。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 この例では、SharePoint プロジェクト サービスを使用して、取得、 <xref:EnvDTE.DTE> Visual Studio で開くために使用するオブジェクトを一覧表示します。 SharePoint プロジェクト サービスの詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して、](../sharepoint/using-the-sharepoint-project-service.md)します。  
  
 拡張機能の SharePoint ノードを作成する基本的なタスクの詳細については、次を参照してください。[方法。サーバー エクスプ ローラーでの SharePoint ノードを拡張](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)します。  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>拡張機能をデプロイします。  
 展開する、**サーバー エクスプ ローラー**拡張機能、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張します。](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [SharePoint プロジェクト サービスを使用します。](../sharepoint/using-the-sharepoint-project-service.md)   
 [Visual Studio の SharePoint ツールの拡張機能をデプロイします。](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
