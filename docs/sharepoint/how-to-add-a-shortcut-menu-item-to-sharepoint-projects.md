---
title: "方法: SharePoint プロジェクトへのショートカット メニュー項目の追加 |Microsoft ドキュメント"
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: bb251fe9-f1bf-4ddd-9359-4b7f78fbd50f
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0e327a716fc77dbc8dd3515c092dcd32c2da5158
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>方法: ショートカット メニュー項目を SharePoint プロジェクトに追加する
  ショートカット メニュー項目は、任意の SharePoint プロジェクトに追加できます。 プロジェクト ノードを右クリックしたときに、メニュー項目が表示されます**ソリューション エクスプ ローラー**です。  
  
 次の手順では、プロジェクトの拡張機能が既に作成されたことを前提としています。 詳細については、次を参照してください。[する方法: SharePoint プロジェクトの拡張機能を作成する](../sharepoint/how-to-create-a-sharepoint-project-extension.md)です。  
  
### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>SharePoint プロジェクトにショートカット メニュー項目を追加するには  
  
1.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>のメソッド、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>実装、ハンドル、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested>のイベント、 *projectService*パラメーター。  
  
2.  イベント ハンドラーで、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested>イベント、新しい<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>オブジェクトを<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A>または<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A>イベント引数のパラメーターのコレクション。  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> 、新しいイベント ハンドラー<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>オブジェクト、ユーザーが、ショートカット メニュー項目をクリックしたときに実行するタスクを実行します。  
  
## <a name="example"></a>例  
 次のコード例は、SharePoint プロジェクトのノードにショートカット メニュー項目を追加する方法を示します**ソリューション エクスプ ローラー**です。 ユーザーがプロジェクト ノードを右クリックし、クリックして、**メッセージを出力ウィンドウに書き込む**メニュー項目、Visual Studio でのメッセージが表示されます、**出力**ウィンドウです。 この例では、SharePoint プロジェクト サービスを使用して、メッセージが表示されます。 詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して](../sharepoint/using-the-sharepoint-project-service.md)です。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照を含むクラス ライブラリ プロジェクトが必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>拡張機能の配置  
 拡張機能を展開するには、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint プロジェクトの拡張](../sharepoint/extending-sharepoint-projects.md)   
 [方法: SharePoint プロジェクトの拡張機能を作成します。](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [方法: SharePoint プロジェクトにプロパティを追加する](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  