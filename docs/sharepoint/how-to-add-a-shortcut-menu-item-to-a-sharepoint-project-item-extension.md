---
title: "方法: SharePoint プロジェクト項目の拡張機能のショートカット メニュー項目の追加 |Microsoft ドキュメント"
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: d00513a6-d66d-4fbe-9efa-ef3b08c9a73a
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7c3cb29fa90917f50b42579bf6f274aa8a20d99f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>方法: ショートカット メニュー項目を SharePoint プロジェクト項目の拡張機能に追加する
  プロジェクト項目の拡張機能を使用して、既存の SharePoint プロジェクト項目にショートカット メニュー項目を追加できます。 プロジェクト項目を右クリックしたときに、メニュー項目が表示されます**ソリューション エクスプ ローラー**です。  
  
 次の手順では、プロジェクト項目の拡張機能が既に作成されたことを前提としています。 詳細については、次を参照してください。[する方法: SharePoint プロジェクト項目の拡張機能を作成する](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)です。  
  
### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>プロジェクト項目の拡張機能のショートカット メニュー項目を追加するには  
  
1.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>のメソッド、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>実装、ハンドル、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>のイベント、 *projectItemType*パラメーター。  
  
2.  イベント ハンドラーで、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>イベント、新しい<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>オブジェクトを<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A>または<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A>イベント引数のパラメーターのコレクション。  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> 、新しいイベント ハンドラー<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>オブジェクト、ユーザーが、ショートカット メニュー項目をクリックしたときに実行するタスクを実行します。  
  
## <a name="example"></a>例  
 次のコード例では、イベント レシーバー プロジェクト項目にショートカット メニュー項目を追加する方法を示します。 ユーザーが内のプロジェクト項目を右クリックしたとき**ソリューション エクスプ ローラー**をクリックして、**メッセージを出力ウィンドウに書き込む**メニュー項目、Visual Studio でのメッセージが表示されます、**出力**ウィンドウです。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]  
  
 この例では、SharePoint プロジェクト サービスを使用するメッセージを記述して、**出力**ウィンドウです。 詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して](../sharepoint/using-the-sharepoint-project-service.md)です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照を含むクラス ライブラリ プロジェクトが必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>拡張機能の配置  
 拡張機能を展開するには、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: SharePoint プロジェクト項目の拡張機能を作成します。](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [方法: SharePoint プロジェクト項目の拡張機能にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [SharePoint プロジェクト項目の拡張](../sharepoint/extending-sharepoint-project-items.md)   
 [チュートリアル: SharePoint プロジェクト項目の種類の拡張](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  