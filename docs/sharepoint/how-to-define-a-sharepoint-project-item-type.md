---
title: "方法: SharePoint プロジェクト項目の種類の定義 |Microsoft ドキュメント"
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
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: 18b56e7c-4efb-47a2-abfc-e9018ae38267
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2c5f39fea52b6f417b046a7ff1f72dff1190a038
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>方法: SharePoint プロジェクト項目の種類を定義する
  カスタム SharePoint プロジェクト項目を作成する場合は、プロジェクト項目の種類を定義します。 詳細については、次を参照してください。[カスタム SharePoint プロジェクト項目の種類を定義する](../sharepoint/defining-custom-sharepoint-project-item-types.md)です。  
  
### <a name="to-define-a-project-item-type"></a>プロジェクト項目の種類を定義するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> インターフェイスを実装するクラスを作成します。  
  
4.  クラスに次の属性を追加します。  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>。 この属性により、Visual Studio を検出して読み込む、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>実装します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>属性コンス トラクターの型。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 プロジェクト アイテム型定義では、この属性は、新しいプロジェクト項目の文字列識別子を指定します。 形式を使用することをお勧め*会社名*.*機能名*すべてのプロジェクト項目の一意の名前であるかどうかを確認します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>。 この属性は、このプロジェクト アイテムに表示するアイコンを指定**ソリューション エクスプ ローラー**です。 この属性は省略可能です。適用されませんが、クラス、Visual Studio は、プロジェクト項目の既定のアイコンを表示します。 この属性を設定する場合は、アイコンやアセンブリに埋め込まれているビットマップの完全修飾名を渡します。  
  
5.  実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>メソッドを使用するメンバーの*projectItemTypeDefinition*プロジェクト項目の種類の動作を定義するパラメーターです。 このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>で定義されたイベントへのアクセスを提供するオブジェクト、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>インターフェイスです。 プロジェクト項目の種類の特定のインスタンスにアクセスするには、処理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>ようなイベント<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>です。  
  
## <a name="example"></a>例  
 次のコード例では、単純なプロジェクト項目の種類を定義する方法を示します。 このプロジェクト項目の種類にメッセージを書き込みます、**出力**ウィンドウと**エラー一覧**ウィンドウのユーザーがこの種類のプロジェクト項目をプロジェクトに追加します。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]  
  
 この例では、SharePoint プロジェクト サービスを使用するメッセージを記述して、**出力**ウィンドウと**エラー一覧**ウィンドウです。 詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して](../sharepoint/using-the-sharepoint-project-service.md)です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>プロジェクト項目の展開  
 プロジェクト項目を使用するには、他の開発者を有効にするには、プロジェクト テンプレートまたはプロジェクト項目テンプレートを作成します。 詳細については、次を参照してください。[項目テンプレートを作成し、SharePoint プロジェクト項目用のプロジェクト テンプレート](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)です。  
  
 プロジェクト項目を展開するには、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]拡張機能 (VSIX) に、アセンブリ、テンプレート、およびその他のファイル プロジェクト項目と共に配布するパッケージ化します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目  
 [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [SharePoint プロジェクト項目の項目テンプレートとプロジェクト テンプレートを作成します。](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [チュートリアル: 項目テンプレート、第 1 部にカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [チュートリアル: プロジェクト テンプレート、第 1 部に基づくサイト列プロジェクト項目の作成](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [方法: カスタム SharePoint プロジェクト項目の種類にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [方法: ショートカット メニュー項目をカスタム SharePoint プロジェクト項目の種類に追加する](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  