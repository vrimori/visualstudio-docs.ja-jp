---
title: "Extending SharePoint Project Items"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Extending SharePoint Project Items
  既に Visual Studio にインストールされている種類の SharePoint プロジェクト項目に機能を追加する必要がある場合は、プロジェクト項目の拡張機能を作成します。  たとえば、Visual Studio の組み込みの**イベント レシーバー**または**リスト定義**に対する拡張機能を作成したり、カスタム プロジェクト項目の種類に対する拡張機能を作成したりできます。  また、すべての種類の SharePoint プロジェクト項目の拡張機能を作成することもできます。  
  
## SharePoint プロジェクト項目の拡張のタスク  
 プロジェクト項目を拡張するには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> インターフェイスを実装する Visual Studio 拡張機能アセンブリを構築します。  詳細については、「[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)」を参照してください。  
  
 プロジェクト項目を拡張する場合は、プロジェクト項目に次の機能も追加できます。  
  
-   ショートカット メニュー項目をプロジェクト項目の種類に追加する。  メニュー項目は **\[ソリューション エクスプローラー\]**プロジェクト項目に対するショートカット メニューを開いたときに表示されます。  プロジェクト項目を右クリックするか、を選択し、Shift \+ F10キーを選択すると、ショートカット メニューが開きます。  詳細については、「[How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)」を参照してください。  
  
-   プロジェクト項目にカスタム プロパティを追加する。  プロパティは **\[プロパティ\]** のウィンドウで **\[ソリューション エクスプローラー\]**のプロジェクト項目を選択するときに表示されます。  詳細については、「[How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)」を参照してください。  
  
 プロジェクト項目の拡張機能の作成、配置、およびテストの方法については、「[Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)」を参照してください。  
  
## プロジェクト項目の拡張機能とプロジェクト項目のインスタンスとの関係について  
 プロジェクト項目の拡張機能を作成するときに、関連付けられている種類のプロジェクト項目が SharePoint プロジェクトに追加されると、Visual Studio によって拡張機能が読み込まれます。  たとえば、**イベント レシーバー** プロジェクト項目の拡張機能を作成すると、プロジェクトに**イベント レシーバー** プロジェクト項目を追加したときに、Visual Studio によって拡張機能が読み込まれます。  Visual Studio は、関連付けられているプロジェクト項目の種類のすべてのインスタンスの拡張機能と同一のインスタンスを読み込みます。  前の例では、ユーザーがプロジェクトに 2 つ目の**イベント レシーバー** プロジェクト項目を追加すると、拡張機能の同一インスタンスを使用し、2 つ目のプロジェクト項目がカスタマイズされます。  
  
 拡張するプロジェクト項目の種類の特定のインスタンスにアクセスするには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> メソッドの実装で、*projectItemType* パラメーターの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> イベントの 1 つを処理します。  たとえば、拡張の対象となっている種類のプロジェクト項目がどの時点でプロジェクトに追加されるかを判断するには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> イベントを処理します。  詳細については、「[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)」を参照してください。  
  
## SharePoint プロジェクト項目の識別子  
 それぞれの SharePoint プロジェクト項目には、対応する文字列識別子があります。  次のようなタスクを実行する場合は、プロジェクト項目の識別子を知っておく必要があります。  
  
-   プロジェクト項目の拡張機能を作成する。  この場合、拡張の対象となるプロジェクト項目の識別子を <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> のコンストラクターに渡す必要があります。  すべてのプロジェクト項目の種類の拡張機能を作成するには、**\*** 文字列値を渡します。  
  
-   プロジェクト項目をプログラムによってプロジェクトに追加する。  この場合、プロジェクト項目の識別子を <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> メソッドに渡す必要があります。  
  
 Visual Studio に付属する SharePoint プロジェクト項目の識別子を次の表に示します。  
  
|プロジェクト項目の名前|文字列識別子|  
|-----------------|------------|  
|ビジネス データ カタログ モデル|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|コンテンツ タイプ|Microsoft.VisualStudio.SharePoint.ContentType|  
|イベント レシーバー|Microsoft.VisualStudio.SharePoint.EventHandler|  
|空の要素|Microsoft.VisualStudio.SharePoint.GenericElement|  
|リスト定義<br /><br /> コンテンツ タイプに基づくリスト定義|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|リスト インスタンス|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Module|Microsoft.VisualStudio.SharePoint.Module|  
|シーケンシャル ワークフロー<br /><br /> ステート マシン ワークフロー|Microsoft.VisualStudio.SharePoint.Workflow|  
|サイト定義|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|可視 Web パーツ|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Web パーツ|Microsoft.VisualStudio.SharePoint.WebPart|  
|ワークフロー関連付けフォーム|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## 参照  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  