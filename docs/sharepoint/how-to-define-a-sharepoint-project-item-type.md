---
title: '方法: SharePoint プロジェクト項目の種類の定義 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bfb04256a1bb8aacb062f30839566b75b599a3a3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872028"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>方法: SharePoint プロジェクト項目の種類を定義します。
  カスタム SharePoint プロジェクト項目を作成する場合は、プロジェクト項目の種類を定義します。 詳細については、次を参照してください。[カスタム SharePoint プロジェクト項目の種類を定義する](../sharepoint/defining-custom-sharepoint-project-item-types.md)します。  
  
### <a name="to-define-a-project-item-type"></a>プロジェクト項目の種類を定義するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> インターフェイスを実装するクラスを作成します。  
  
4.  クラスには、次の属性を追加します。  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>。 この属性により、Visual Studio を検出して読み込む、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>実装します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>属性コンス トラクターの型。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 プロジェクト項目の型定義では、この属性は、新しいプロジェクト項目の文字列識別子を指定します。 形式を使用することをお勧めします*会社名*。 *。機能名*すべてのプロジェクト項目の一意の名前であるかどうかを確認します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>。 この属性では、このプロジェクト項目に対して表示するアイコンを指定する**ソリューション エクスプ ローラー**します。 この属性は省略可能です。適用されませんが、クラス、Visual Studio には、プロジェクト項目の既定のアイコンが表示されます。 この属性を設定する場合は、アイコンまたはビットマップがアセンブリに埋め込むの完全修飾名を渡します。  
  
5.  実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>メソッドのメンバーを使用して、 *projectItemTypeDefinition*プロジェクト項目の種類の動作を定義するパラメーター。 このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>で定義されたイベントへのアクセスを提供するオブジェクト、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>インターフェイス。 プロジェクト項目の種類の特定のインスタンスにアクセスするには、処理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>ようなイベント<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>します。  
  
## <a name="example"></a>例  
 次のコード例では、単純なプロジェクト項目の種類を定義する方法を示します。 このプロジェクト項目の種類へのメッセージを書き込みます、**出力**ウィンドウと**エラー一覧**ウィンドウ ユーザーがこの種類のプロジェクト項目をプロジェクトに追加します。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]  
  
 この例では、SharePoint プロジェクト サービスを使用して、メッセージを書き込む、**出力**ウィンドウと**エラー一覧**ウィンドウ。 詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して、](../sharepoint/using-the-sharepoint-project-service.md)します。  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>プロジェクト項目を配置します。  
 他の開発者が自分のプロジェクト項目を有効にするには、プロジェクト テンプレートまたはプロジェクト項目テンプレートを作成します。 詳細については、次を参照してください。[項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成する](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)します。  
  
 プロジェクト項目を展開するには、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]拡張機能 (VSIX) に、アセンブリ、テンプレート、およびその他のファイル プロジェクト項目に配布するパッケージ化します。 詳細については、次を参照してください。 [、SharePoint 用の拡張機能の展開ツールの Visual Studio で](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成します。](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [チュートリアル: 項目テンプレート、第 1 部でのカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [チュートリアル: プロジェクト テンプレート、第 1 部でサイト列プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [方法: カスタム SharePoint プロジェクト項目の種類にプロパティを追加します。](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [方法: カスタム SharePoint プロジェクト項目の種類のショートカット メニュー項目を追加します。](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
