---
title: SharePoint プロジェクト項目の拡張 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ecb6df8b7d6207336404d5e2f7562a88a18895bc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872587"
---
# <a name="extend-sharepoint-project-items"></a>SharePoint プロジェクト項目を拡張します。
  Visual Studio で既にインストールされている SharePoint プロジェクト項目の種類に機能を追加する場合は、プロジェクト項目の拡張機能を作成します。 たとえば、組み込みの拡張機能を作成できます**イベント レシーバー**または**リスト定義**プロジェクト項目を Visual Studio またはカスタム プロジェクト項目の種類の拡張機能を作成することができます。 すべての種類の SharePoint プロジェクト項目の拡張機能を作成することもできます。  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>SharePoint プロジェクト項目を拡張するためのタスク
 プロジェクト項目を拡張するアセンブリをビルドする Visual Studio 拡張機能を実装する、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>インターフェイス。 詳細については、「[方法 :SharePoint プロジェクト項目の拡張機能作成](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)です。  
  
 プロジェクト項目を拡張するときは、プロジェクト項目に、次の機能を追加することもできます。  
  
- プロジェクト項目にショートカット メニュー項目を追加します。 プロジェクト項目のショートカット メニューを開くと、メニュー項目が表示される**ソリューション エクスプ ローラー**します。 プロジェクト アイテムを右クリックしてまたは選択するかを選択し、ショートカット メニューを開き、 **Shift**+**F10**キー。 詳細については、「[方法 :SharePoint プロジェクト項目の拡張機能のショートカット メニュー項目の追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)します。  
  
- プロジェクト項目にカスタム プロパティを追加します。 プロパティを表示する、**プロパティ**ウィンドウで、プロジェクト項目を選択すると**ソリューション エクスプ ローラー**します。 詳細については、「[方法 :SharePoint プロジェクト項目の拡張機能にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)します。  
  
  作成、展開、およびプロジェクト項目の拡張機能をテストする方法について説明するチュートリアルでは、次を参照してください。[チュートリアル。SharePoint プロジェクト項目の種類の拡張](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)します。  
  
## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>プロジェクト項目の拡張機能とプロジェクト項目のインスタンス間のリレーションシップを理解します。
 プロジェクト項目の拡張機能を作成するときに、Visual Studio は、SharePoint プロジェクトに関連付けられている型のプロジェクト項目が追加されたときに、拡張機能を読み込みます。 拡張機能を作成する場合など**イベント レシーバー**プロジェクト項目では、Visual Studio 拡張機能を読み込むユーザーを追加するとき、**イベント レシーバー**プロジェクトにプロジェクト項目。 Visual Studio では、関連付けられているプロジェクト項目の種類のすべてのインスタンス拡張機能の同じインスタンスを使用します。 ユーザーが 2 つ目を追加する場合、前の例で**イベント レシーバー**プロジェクト項目をプロジェクトには、2 つ目のプロジェクト項目をカスタマイズする、拡張機能の同じインスタンスを使用します。  
  
 拡張するプロジェクト項目の種類の特定のインスタンスにアクセスするのいずれかの処理、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>のイベント、 *projectItemType*パラメーターの実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>メソッド。 たとえば、処理を拡張する型のプロジェクト項目をプロジェクトに追加する場合を判断する、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>イベント。 詳細については、「[方法 :SharePoint プロジェクト項目の拡張機能作成](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)です。  
  
## <a name="identifiers-for-sharepoint-project-items"></a>SharePoint プロジェクト アイテムの識別子
 各 SharePoint プロジェクト アイテムには、対応する文字列識別子があります。 次のタスクを実行する場合は、プロジェクト項目の識別子をおく必要があります。  
  
- プロジェクト項目の拡張機能を作成します。 この場合は、コンス トラクターに拡張するプロジェクト項目の識別子を渡す必要があります、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>します。 プロジェクト項目の種類のすべての拡張機能を作成するには、渡す、 **\\*** 文字列値。  
  
- プログラムで、プロジェクト項目をプロジェクトに追加します。 この場合、プロジェクト項目の識別子を渡す必要があります、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A>メソッド。  
  
  次の表では、Visual Studio に含まれている SharePoint プロジェクト アイテムの識別子を示します。  
  
|プロジェクト項目の名前|文字列の識別子|  
|-----------------------|-----------------------|  
|ビジネス データ カタログのモデル|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|コンテンツ タイプ|Microsoft.VisualStudio.SharePoint.ContentType|  
|イベント レシーバー|Microsoft.VisualStudio.SharePoint.EventHandler|  
|空の要素|Microsoft.VisualStudio.SharePoint.GenericElement|  
|リスト定義<br /><br /> コンテンツ タイプからリストの定義|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|リスト インスタンス|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Module|Microsoft.VisualStudio.SharePoint.Module|  
|シーケンシャル ワークフロー<br /><br /> ステート マシン ワークフロー|Microsoft.VisualStudio.SharePoint.Workflow|  
|サイト定義|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|可視 Web パーツ|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Web パーツ|Microsoft.VisualStudio.SharePoint.WebPart|  
|ワークフロー関連付けフォーム|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>関連項目
 [方法: SharePoint プロジェクト項目の拡張機能を作成します。](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [方法: SharePoint プロジェクト項目の拡張機能のショートカット メニュー項目を追加します。](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [方法: SharePoint プロジェクト項目の拡張機能にプロパティを追加します。](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [チュートリアル: SharePoint プロジェクト項目の種類を拡張します。](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [SharePoint プロジェクト システムを拡張します。](../sharepoint/extending-the-sharepoint-project-system.md)  
