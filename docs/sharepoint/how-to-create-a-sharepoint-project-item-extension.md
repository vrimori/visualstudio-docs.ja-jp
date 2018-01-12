---
title: "方法: SharePoint プロジェクト項目の拡張機能を作成 |Microsoft ドキュメント"
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d4a5aa0b7e40ddca0281ce92c3bbf9946238403e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>方法: SharePoint プロジェクト項目の拡張機能を作成する
  Visual Studio で既にインストールされている SharePoint プロジェクト項目に機能を追加する場合は、プロジェクト項目の拡張機能を作成します。 詳細については、次を参照してください。 [SharePoint プロジェクト項目の拡張](../sharepoint/extending-sharepoint-project-items.md)です。  
  
### <a name="to-create-a-project-item-extension"></a>プロジェクト項目の拡張機能を作成するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> インターフェイスを実装するクラスを作成します。  
  
4.  クラスに次の属性を追加します。  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>。 この属性により、Visual Studio を検出して読み込む、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>実装します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>属性コンス トラクターの型。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 プロジェクト項目の拡張機能では、この属性は、拡張するプロジェクト アイテムを識別します。 プロジェクト項目の ID を属性コンス トラクターに渡します。 Visual Studio に含まれているプロジェクト項目の Id の一覧は、次を参照してください。 [SharePoint プロジェクト項目の拡張](../sharepoint/extending-sharepoint-project-items.md)です。  
  
5.  実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>メソッドを使用するメンバーの*projectItemType*拡張機能の動作を定義するパラメーターです。 このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>で定義されたイベントへのアクセスを提供するオブジェクト、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>インターフェイスです。 拡張するプロジェクト項目の種類の特定のインスタンスにアクセスするには、処理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>ようなイベント<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>です。  
  
## <a name="example"></a>例  
 次のコード例では、イベント レシーバー プロジェクト項目の単純な拡張機能を作成する方法を示します。 たびに、ユーザーは、SharePoint プロジェクトに、イベント レシーバー プロジェクト項目を追加、この拡張機能、メッセージを書き込みます、**出力**ウィンドウと**エラー一覧**ウィンドウです。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]  
  
 この例では、SharePoint プロジェクト サービスを使用するメッセージを記述して、**出力**ウィンドウと**エラー一覧**ウィンドウです。 詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して](../sharepoint/using-the-sharepoint-project-service.md)です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>拡張機能の配置  
 拡張機能を展開するには、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>参照  
 [SharePoint プロジェクト項目の拡張](../sharepoint/extending-sharepoint-project-items.md)   
 [チュートリアル: SharePoint プロジェクト項目の種類の拡張](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  