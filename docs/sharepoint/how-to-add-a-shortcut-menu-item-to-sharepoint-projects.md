---
title: '方法: SharePoint プロジェクトのショートカット メニュー項目の追加 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ba38984b5c49dbf834286414e61734fe46069876
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964138"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>方法: SharePoint プロジェクトのショートカット メニュー項目を追加します。
  SharePoint プロジェクトのショートカット メニュー項目を追加できます。 プロジェクト ノードを右クリックしたときに、メニュー項目が表示されます**ソリューション エクスプ ローラー**します。  
  
 次の手順では、プロジェクトの拡張機能を既に作成したことを前提としています。 詳細については、「[方法 :SharePoint プロジェクト拡張機能作成](../sharepoint/how-to-create-a-sharepoint-project-extension.md)です。  
  
### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>ショートカット メニュー項目を SharePoint プロジェクトに追加するには  
  
1.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>のメソッド、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>実装、ハンドル、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested>のイベント、 *projectService*パラメーター。  
  
2.  イベント ハンドラーで、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested>イベントを追加する新しい<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>オブジェクトを<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A>または<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A>イベント引数のパラメーターのコレクション。  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>新しいイベント ハンドラー<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>オブジェクト、ユーザーがクリックして、ショートカット メニュー項目を実行するタスクを実行します。  
  
## <a name="example"></a>例  
 次のコード例は、SharePoint プロジェクト ノードにショートカット メニュー項目を追加する方法を示します**ソリューション エクスプ ローラー**します。 ユーザーがプロジェクト ノードを右クリックし、クリックして、**出力ウィンドウにメッセージを書き込む**メニュー項目では、Visual Studio でのメッセージが表示されます、**出力**ウィンドウ。 この例では、SharePoint プロジェクト サービスを使用して、メッセージが表示されます。 詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して、](../sharepoint/using-the-sharepoint-project-service.md)します。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照を含むクラス ライブラリ プロジェクトが必要です。  
  
-   Microsoft.VisualStudio.SharePoint
-     
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>拡張機能をデプロイします。  
 拡張機能を展開するには、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクトを拡張します。](../sharepoint/extending-sharepoint-projects.md)   
 [方法: SharePoint プロジェクト拡張機能を作成します。](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [方法: SharePoint プロジェクトにプロパティを追加します。](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
