---
title: "Defining Custom SharePoint Project Item Types"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: be300c24-fd1b-4fc7-a4e9-a5df1d81d3fc
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Defining Custom SharePoint Project Item Types
  新しい種類の SharePoint プロジェクト項目を作成する必要がある場合は、新しい SharePoint プロジェクト項目の種類を定義します。  たとえば、Visual Studio には、SharePoint サイトにフィールドまたはカスタム動作を追加するための SharePoint プロジェクト項目は含まれていません。  フィールド、カスタム動作、またはその他の種類の SharePoint コンポーネントを作成するための SharePoint プロジェクト項目の独自の種類を定義できます。  
  
## SharePoint プロジェクト項目の種類を定義するためのタスク  
 カスタム プロジェクト項目を定義するには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> インターフェイスを実装する Visual Studio 拡張機能アセンブリを構築します。  詳細については、「[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)」を参照してください。  
  
 カスタム プロジェクト項目の種類を定義する場合は、プロジェクト項目に次の機能も追加できます。  
  
-   ショートカット メニュー項目をプロジェクト項目の種類に追加する。  メニュー項目は、を選択し、Shift \+ F10キーをかを選択できます。プロジェクト項目を右クリックするか、によって **\[ソリューション エクスプローラー\]** プロジェクト項目に対するショートカット メニューを開いたときに表示されます。  詳細については、「[How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)」を参照してください。  
  
-   プロジェクト項目にカスタム プロパティを追加する。  プロパティは **\[プロパティ\]** のウィンドウで **\[ソリューション エクスプローラー\]**のプロジェクト項目を選択するときに表示されます。  詳細については、「[How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)」を参照してください。  
  
 自分が作成したプロジェクト項目を、他の開発者が Visual Studio で使用できるようにするには、.spdata ファイルを作成し、プロジェクト項目に関連する項目テンプレートまたはプロジェクト テンプレートを作成します。  詳細については、「[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)」を参照してください。  
  
## プロジェクト項目の種類とプロジェクト項目のインスタンスとの関係について  
 SharePoint プロジェクト項目の種類を定義するときに、関連付けられている種類のプロジェクト項目が SharePoint プロジェクトに追加されると、Visual Studio によって拡張機能が読み込まれます。  たとえば、新しい**カスタム アクション** プロジェクト項目の種類を定義する場合は、ユーザーがプロジェクトに**カスタム アクション** プロジェクト項目を追加したときに、Visual Studio によって拡張機能が読み込まれます。  Visual Studio は、関連付けられているプロジェクト項目の種類のすべてのインスタンスの拡張機能と同一のインスタンスを読み込みます。  前の例では、ユーザーがプロジェクトに 2 つ目の**カスタム アクション** プロジェクト項目を追加すると、拡張機能の同一インスタンスを使用し、2 つ目のプロジェクト項目がカスタマイズされます。  
  
 プロジェクト項目の種類の特定のインスタンスにアクセスするには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> メソッドの実装で、*projectItemTypeDefinition* パラメーターの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> イベントの 1 つを処理します。  たとえば、独自の種類のプロジェクト項目がどの時点でプロジェクトに追加されるかを判断するには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> イベントを処理します。  詳細については、「[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)」を参照してください。  
  
## 参照  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 1&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 2&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  