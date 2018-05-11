---
title: SharePoint プロジェクト項目を拡張 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1cc202b2e3e303f8f6e92b82bbfbc6f5525966bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="extending-sharepoint-project-items"></a>SharePoint プロジェクト項目の拡張
  Visual Studio で既にインストールされている SharePoint プロジェクト項目の種類に機能を追加する場合は、プロジェクト項目の拡張機能を作成します。 たとえば、組み込みの拡張機能を作成することができます**イベント レシーバー**または**リスト定義**のプロジェクトが Visual Studio で、項目またはカスタム プロジェクト項目の種類の拡張機能を作成することができます。 すべての SharePoint プロジェクト項目の種類の拡張機能を作成することもできます。  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>SharePoint プロジェクト項目を拡張するためのタスク  
 プロジェクト項目を拡張するアセンブリをビルドする Visual Studio 拡張機能を実装する、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>インターフェイスです。 詳細については、次を参照してください。[する方法: SharePoint プロジェクト項目の拡張機能を作成する](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)です。  
  
 プロジェクト項目を拡張する場合に、プロジェクト項目に、次の機能を追加することもできます。  
  
-   プロジェクト項目にショートカット メニュー項目を追加します。 プロジェクト項目のショートカット メニューを開くと、メニュー項目が表示される**ソリューション エクスプ ローラー**です。 プロジェクト項目を右クリックして、ショートカット メニューを開くか、キーを選択し、shift キーを押しながら F10 を選択します。 詳細については、次を参照してください。[する方法: SharePoint プロジェクト項目の拡張機能にショートカット メニュー項目を追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)です。  
  
-   プロジェクト項目にカスタム プロパティを追加します。 このプロパティを表示、**プロパティ**でプロジェクト項目を選択するときにウィンドウ**ソリューション エクスプ ローラー**です。 詳細については、次を参照してください。[する方法: SharePoint プロジェクト項目の拡張機能にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)です。  
  
 作成、配置、およびプロジェクト項目の拡張機能をテストする方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: SharePoint プロジェクト項目の種類の拡張](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)です。  
  
## <a name="understanding-the-relationship-between-project-item-extensions-and-project-item-instances"></a>プロジェクト項目の拡張機能とプロジェクト項目のインスタンス間の関係を理解します。  
 プロジェクト項目の拡張機能を作成するときに、Visual Studio は、関連付けられている型のプロジェクト アイテムが SharePoint プロジェクトに追加されたときに、拡張機能を読み込みます。 たとえば、拡張機能を作成する場合**イベント レシーバー**プロジェクト項目、Visual Studio 拡張機能を読み込む、ユーザーを追加するとき、**イベント レシーバー**プロジェクトにプロジェクト項目です。 Visual Studio では、関連付けられているプロジェクト項目の種類のすべてのインスタンスの拡張機能の同じインスタンスを使用します。 ユーザーが、2 番目を追加する場合、前の例で**イベント レシーバー**プロジェクト項目をプロジェクトには、2 つ目のプロジェクト アイテムをカスタマイズする、拡張機能の同じインスタンスを使用します。  
  
 いずれかの処理を拡張するプロジェクト項目の種類の特定のインスタンスにアクセスするには<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>のイベント、 *projectItemType*の実装でのパラメーター、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>メソッドです。 たとえば、調べるには、プロジェクトの項目を拡張する型をプロジェクトに追加するときに、処理、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>イベント。 詳細については、次を参照してください。[する方法: SharePoint プロジェクト項目の拡張機能を作成する](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)です。  
  
## <a name="identifiers-for-sharepoint-project-items"></a>SharePoint プロジェクト項目の識別子  
 各 SharePoint プロジェクト項目には、対応する文字列識別子があります。 次のタスクを実行する場合、プロジェクト項目の識別子をおく必要があります。  
  
-   プロジェクト項目の拡張機能を作成します。 この例では、コンス トラクターを拡張するプロジェクト項目の識別子を渡す必要があります、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>です。 プロジェクト項目の種類のすべての拡張機能を作成するには、渡す、 **\***文字列値です。  
  
-   プログラムで、プロジェクト項目をプロジェクトに追加します。 この場合、プロジェクト項目の識別子を渡す必要があります、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A>メソッドです。  
  
 次の表は、Visual Studio に含まれる SharePoint プロジェクト項目の識別子を一覧表示します。  
  
|プロジェクト項目の名前|文字列の識別子|  
|-----------------------|-----------------------|  
|ビジネス データ カタログのモデル|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|コンテンツ タイプ|Microsoft.VisualStudio.SharePoint.ContentType|  
|イベント レシーバー|Microsoft.VisualStudio.SharePoint.EventHandler|  
|空の要素|Microsoft.VisualStudio.SharePoint.GenericElement|  
|リストの定義<br /><br /> コンテンツ タイプからリストの定義|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|リスト インスタンス|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Module|Microsoft.VisualStudio.SharePoint.Module|  
|シーケンシャル ワークフロー<br /><br /> ステート マシン ワークフロー|Microsoft.VisualStudio.SharePoint.Workflow|  
|サイト定義|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|可視 Web パーツ|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Web パーツ|Microsoft.VisualStudio.SharePoint.WebPart|  
|ワークフロー関連付けフォーム|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>関連項目  
 [方法: SharePoint プロジェクト項目の拡張機能を作成します。](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [方法: SharePoint プロジェクト項目の拡張機能にショートカット メニュー項目を追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [方法: SharePoint プロジェクト項目の拡張機能にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [チュートリアル: SharePoint プロジェクト項目の種類の拡張](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [SharePoint プロジェクト システムの拡張](../sharepoint/extending-the-sharepoint-project-system.md)  
  