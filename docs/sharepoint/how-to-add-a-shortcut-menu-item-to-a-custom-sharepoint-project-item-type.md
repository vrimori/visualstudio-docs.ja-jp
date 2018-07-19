---
title: '方法: カスタム SharePoint プロジェクト項目の種類のショートカット メニュー項目の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 580839936cfa42b4e76999809cd8917f3eb4f041
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755503"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>方法: ショートカット メニュー項目をカスタム SharePoint プロジェクト項目の種類に追加
  カスタム SharePoint プロジェクト項目の種類を定義するときに、プロジェクト項目にショートカット メニュー項目を追加できます。 プロジェクト項目を右クリックしたときに、メニュー項目が表示されます**ソリューション エクスプ ローラー**します。  
  
 次の手順では、独自の SharePoint プロジェクト項目の種類が既に定義されている前提としています。 詳細については、次を参照してください。[方法: SharePoint プロジェクト項目の種類定義](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)します。  
  
### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>カスタム プロジェクト項目の種類にショートカット メニュー項目を追加するには  
  
1.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>のメソッド、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>実装、ハンドル、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>のイベント、 *projectItemTypeDefinition*パラメーター。  
  
2.  イベント ハンドラーで、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>イベントを追加する新しい<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>オブジェクトを<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A>または<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A>イベント引数のパラメーターのコレクション。  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>新しいイベント ハンドラー<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>オブジェクト、ユーザーは、ショートカット メニュー項目を選択したときに実行するタスクを実行します。  
  
## <a name="example"></a>例  
 次のコード例では、カスタム プロジェクト項目の種類をコンテキスト メニュー項目を追加する方法を示します。 ユーザーが内のプロジェクト項目からショートカット メニューを開く場合**ソリューション エクスプ ローラー**を選択し、**出力ウィンドウにメッセージを書き込む**メニュー項目では、Visual Studio でのメッセージが表示されます、**出力**ウィンドウ。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]  
  
 この例では、SharePoint プロジェクト サービスを使用して、メッセージを書き込む、**出力**ウィンドウ。 詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して、](../sharepoint/using-the-sharepoint-project-service.md)します。  
  
## <a name="compile-the-code"></a>コードをコンパイルします  
 この例では、次のアセンブリへの参照を含むクラス ライブラリ プロジェクトが必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>プロジェクト項目を配置します。  
 他の開発者が自分のプロジェクト項目を有効にするには、プロジェクト テンプレートまたはプロジェクト項目テンプレートを作成します。 詳細については、次を参照してください。[項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成する](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)します。  
  
 プロジェクト項目を展開するには、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]拡張機能 (VSIX) に、アセンブリ、テンプレート、およびその他のファイル プロジェクト項目に配布するパッケージ化します。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [方法: SharePoint プロジェクト項目の種類の定義](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [方法: カスタム SharePoint プロジェクト項目の種類にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
 
