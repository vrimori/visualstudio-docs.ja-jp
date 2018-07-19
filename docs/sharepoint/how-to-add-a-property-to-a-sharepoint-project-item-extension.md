---
title: '方法: SharePoint プロジェクト項目の拡張機能にプロパティを追加 |Microsoft Docs'
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
ms.openlocfilehash: 1af848f432183153707b2debfed563f3a00d4156
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758100"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>方法: SharePoint プロジェクト項目の拡張機能にプロパティを追加
  プロジェクト項目の拡張機能を使用して、Visual Studio で既にインストールされている SharePoint プロジェクト アイテムにプロパティを追加することができます。 プロパティを表示する、**プロパティ**ウィンドウで、プロジェクト項目を選択すると**ソリューション エクスプ ローラー**します。  
  
 次の手順では、プロジェクト項目の拡張機能を既に作成したことを前提としています。 詳細については、次を参照してください。[方法: SharePoint プロジェクト項目の拡張機能作成](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)です。  
  
### <a name="to-add-a-property-to-a-project-item-extension"></a>プロジェクト項目の拡張機能にプロパティを追加するには  
  
1.  プロジェクト項目の種類を追加するプロパティを表すパブリック プロパティを持つクラスを定義します。 プロジェクト項目の種類に複数のプロパティを追加する場合は、同じクラスまたは別のクラスですべてのプロパティを定義できます。  
  
2.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>のメソッド、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>実装、ハンドル、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>のイベント、 *projectItemType*パラメーター。  
  
3.  イベント ハンドラーで、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>イベント、プロパティ、クラスのインスタンスを追加、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A>イベント引数のパラメーターのコレクション。  
  
## <a name="example"></a>例  
 次のコード例は、という名前のプロパティを追加する方法を示します**プロパティの例**イベント レシーバー プロジェクト項目にします。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]  
  
### <a name="understand-the-code"></a>コードを理解します。  
 同じインスタンスを確実に、`CustomProperties`クラスには、毎回、使用、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>イベントが発生する、プロパティ オブジェクトを追加するコード例、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>プロジェクト最初の項目にこのイベントが発生するプロパティ。 コードは、このイベントが発生するたびに、このオブジェクトを取得します。 使用しての詳細については、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>にデータをプロジェクト項目に関連付けるプロパティを参照してください[ツールの拡張機能を SharePoint でカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)します。  
  
 プロパティの値に変更を保持する、**設定**のアクセサー`ExampleProperty`に新しい値を保存、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>プロパティが関連付けられているオブジェクト。 使用しての詳細については、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>プロジェクトの項目を含むデータを保持するプロパティを参照してください[SharePoint プロジェクト システムの拡張機能でデータを保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)します。  
  
### <a name="specify-the-behavior-of-custom-properties"></a>カスタム プロパティの動作を指定します。  
 カスタム プロパティの表示し、動作を定義することができます、**プロパティ**ウィンドウからの属性を適用することで、<xref:System.ComponentModel>プロパティ定義に名前空間。 次の属性には、多くのシナリオがあります。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: に表示されるプロパティの名前を指定します、**プロパティ**ウィンドウ。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: の下部に表示される説明文字列を指定します、**プロパティ**、プロパティが選択されている場合は、ウィンドウ。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: プロパティの既定値を指定します。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: カスタムの変換との間に表示される文字列を指定します、**プロパティ**ウィンドウと非文字列プロパティの値。  
  
-   <xref:System.ComponentModel.EditorAttribute>: 使用して、プロパティを変更するカスタム エディターを指定します。  
  
## <a name="compile-the-code"></a>コードをコンパイルします  
 これらの例では、次のアセンブリへの参照を含むクラス ライブラリ プロジェクトが必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>拡張機能をデプロイします。  
 拡張機能を展開するには、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [方法: SharePoint プロジェクト項目の拡張機能の作成](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [方法: SharePoint プロジェクト項目の拡張機能のショートカット メニュー項目の追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [SharePoint プロジェクト項目を拡張します。](../sharepoint/extending-sharepoint-project-items.md)   
 [チュートリアル: SharePoint プロジェクト項目の種類を拡張します。](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  
