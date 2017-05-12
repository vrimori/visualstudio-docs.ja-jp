---
title: "How to: Define a SharePoint Project Item Type"
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
ms.assetid: 18b56e7c-4efb-47a2-abfc-e9018ae38267
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# How to: Define a SharePoint Project Item Type
  カスタムの SharePoint プロジェクト項目を作成する場合は、プロジェクト項目の種類を定義します。  詳細については、「[Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)」を参照してください。  
  
### プロジェクト項目の種類を定義するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> インターフェイスを実装するクラスを作成します。  
  
4.  クラスに次の属性を追加します。  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Visual Studio は、この属性を頼りに <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> の実装を発見し、読み込みます。  この属性のコンストラクターには <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 型を渡します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  プロジェクト項目の種類を定義する際は、新しいプロジェクト項目の文字列識別子をこの属性によって指定します。  プロジェクト項目の名前が重複しないよう、「*\<会社名\>*.*\<機能名\>*」という形式を使用することをお勧めします。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>.  **ソリューション エクスプローラー**に表示されるプロジェクト項目のアイコンは、この属性によって指定されます。  この属性は省略可能です。この属性をクラスに適用しなかった場合は、既定のアイコンを使用してプロジェクト項目が表示されます。  この属性を設定する場合は、アセンブリに埋め込まれているアイコンまたはビットマップの完全修飾名を渡します。  
  
5.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> メソッドの実装では、*projectItemTypeDefinition* パラメーターのメンバーを使用してプロジェクト項目の種類の動作を定義します。  このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> インターフェイスおよび <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> インターフェイスに定義されているイベントにアクセスできる <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> オブジェクトです。  プロジェクト項目の種類の特定インスタンスにアクセスするには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> などの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> イベントを処理します。  
  
## 例  
 次のコード例は、単純なプロジェクト項目の種類を定義する方法を示します。  このプロジェクト項目の種類では、ユーザーがこの種類のプロジェクト項目をプロジェクトに追加すると、**\[出力\]** ウィンドウと **\[エラー一覧\]** ウィンドウにメッセージを書き込みます。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemtype.cs#2)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemtype.vb#2)]  
  
 この例では、SharePoint プロジェクト サービスを使用して、**出力**ウィンドウおよび **\[エラー一覧\]** ウィンドウにメッセージを書き込みます。  詳細については、「[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)」を参照してください。  
  
## コードのコンパイル  
 この例は、次のアセンブリへの参照を必要とします。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## プロジェクト項目の配置  
 自分が定義したプロジェクト項目を他の開発者が使用できるようにするには、プロジェクト テンプレートまたはプロジェクト項目テンプレートを作成します。  詳細については、「[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)」を参照してください。  
  
 プロジェクト項目を配置するには、同梱する必要のあるアセンブリやテンプレート、各種ファイルの [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 拡張機能 \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 1&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  