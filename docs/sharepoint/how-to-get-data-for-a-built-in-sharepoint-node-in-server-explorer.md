---
title: "方法: サーバー エクスプ ローラーで組み込みの SharePoint ノードのデータ取り出し |Microsoft ドキュメント"
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
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b61003516d7551c99f6e265ca2eeced9226958df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>方法: サーバー エクスプローラーの組み込みの SharePoint ノードのデータを取得する
  組み込みの SharePoint ノードごとに**サーバー エクスプ ローラー**ノードが表す基になる SharePoint コンポーネントのデータを取得することができます。 詳細については、次を参照してください。[サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張する](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)です。  
  
## <a name="example"></a>例  
 次のコード例は、リストのノードが表す基になっている SharePoint リストのデータを取得する方法を示します**サーバー エクスプ ローラー**です。 既定では、一覧のノードにある、**ブラウザーで表示**コンテキスト メニュー項目をリストを開く Web ブラウザーでクリックします。 この例では、一覧のノードを拡張を追加して、 **Visual Studio でのビュー**コンテキスト メニュー項目を直接 Visual Studio でのリストを開きます。 コードでは、リスト ボックスの一覧を開くには Visual Studio での URL を取得するノードのデータにアクセスします。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 この例では、SharePoint プロジェクト サービスを使用して、取得、 <xref:EnvDTE.DTE> Visual Studio で開くために使用できるオブジェクトを一覧表示します。 SharePoint プロジェクト サービスの詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して](../sharepoint/using-the-sharepoint-project-service.md)です。  
  
 拡張機能の SharePoint ノードを作成する基本的なタスクの詳細については、次を参照してください。[する方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>拡張機能の配置  
 展開する、**サーバー エクスプ ローラー**拡張機能、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目  
 [サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [SharePoint プロジェクト サービスの使用](../sharepoint/using-the-sharepoint-project-service.md)   
 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  