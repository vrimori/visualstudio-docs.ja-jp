---
title: '方法: SharePoint プロジェクト項目の拡張機能の作成 |Microsoft Docs'
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
ms.openlocfilehash: 93459096e6d88ce3754c32bf7f61a3cf369cbeba
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119876"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>方法: SharePoint プロジェクト項目の拡張機能の作成
  Visual Studio で既にインストールされている SharePoint プロジェクト アイテムに機能を追加する場合は、プロジェクト項目の拡張機能を作成します。 詳細については、次を参照してください。[拡張の SharePoint プロジェクト アイテム](../sharepoint/extending-sharepoint-project-items.md)します。  
  
### <a name="to-create-a-project-item-extension"></a>プロジェクト項目の拡張機能を作成するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> インターフェイスを実装するクラスを作成します。  
  
4.  クラスには、次の属性を追加します。  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>。 この属性により、Visual Studio を検出して読み込む、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>実装します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>属性コンス トラクターの型。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 プロジェクト項目の拡張機能では、この属性は、拡張するプロジェクト項目を識別します。 プロジェクト項目の ID は、属性コンス トラクターに渡します。 Visual Studio に含まれているプロジェクト項目の Id の一覧は、次を参照してください。[拡張の SharePoint プロジェクト アイテム](../sharepoint/extending-sharepoint-project-items.md)します。  
  
5.  実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>メソッドのメンバーを使用して、 *projectItemType*パラメーター、拡張機能の動作を定義します。 このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>で定義されたイベントへのアクセスを提供するオブジェクト、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>インターフェイス。 拡張するプロジェクト項目の種類の特定のインスタンスにアクセスするには、処理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>ようなイベント<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>します。  
  
## <a name="example"></a>例  
 次のコード例では、イベント レシーバー プロジェクト項目の単純な拡張を作成する方法を示します。 毎回ユーザーは、イベント レシーバー プロジェクト項目を SharePoint プロジェクトに追加、この拡張機能は、メッセージを**出力**ウィンドウと**エラー一覧**ウィンドウ。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]  
  
 この例では、SharePoint プロジェクト サービスを使用して、メッセージを書き込む、**出力**ウィンドウと**エラー一覧**ウィンドウ。 詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して、](../sharepoint/using-the-sharepoint-project-service.md)します。  
  
## <a name="compile-the-code"></a>コードをコンパイルします  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>拡張機能をデプロイします。  
 拡張機能を展開するには、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能のデプロイ](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクト項目を拡張します。](../sharepoint/extending-sharepoint-project-items.md)   
 [チュートリアル: SharePoint プロジェクト項目の種類を拡張します。](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  
