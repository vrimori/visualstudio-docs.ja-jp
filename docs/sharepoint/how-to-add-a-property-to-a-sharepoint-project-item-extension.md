---
title: '方法: SharePoint プロジェクト項目の拡張機能にプロパティを追加 |Microsoft ドキュメント'
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
ms.openlocfilehash: d80881d69addd2d1f92bdf2c9b47c6f528945d30
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>方法: SharePoint プロジェクト項目の拡張機能にプロパティを追加する
  プロジェクト項目の拡張機能を使用すると、Visual Studio で既にインストールされている SharePoint プロジェクト項目にプロパティを追加します。 このプロパティを表示、**プロパティ**ウィンドウで、プロジェクト項目を選択すると**ソリューション エクスプ ローラー**です。  
  
 次の手順では、プロジェクト項目の拡張機能が既に作成されたことを前提としています。 詳細については、次を参照してください。[する方法: SharePoint プロジェクト項目の拡張機能を作成する](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)です。  
  
### <a name="to-add-a-property-to-a-project-item-extension"></a>プロジェクト項目の拡張機能にプロパティを追加するには  
  
1.  プロジェクト項目の種類を追加するプロパティを表すパブリック プロパティを持つクラスを定義します。 プロジェクト項目の種類に複数のプロパティを追加する場合は、同じクラスまたは異なるクラスのすべてのプロパティを定義できます。  
  
2.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>のメソッド、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>実装、ハンドル、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>のイベント、 *projectItemType*パラメーター。  
  
3.  イベント ハンドラーで、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>イベント、プロパティ、クラスのインスタンスを追加、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A>イベント引数のパラメーターのコレクション。  
  
## <a name="example"></a>例  
 次のコード例は、という名前のプロパティを追加する方法を示します**Example Property**イベント レシーバー プロジェクト項目にします。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]  
  
### <a name="understanding-the-code"></a>コードをについてください。  
 同じインスタンスのことを確認する、`CustomProperties`クラスには、毎回、使用、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>イベントが発生する、プロパティ オブジェクトを追加するコード例、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>プロジェクト項目の最初のこのイベントの発生時のプロパティです。 コードは、このイベントが再度発生するたびに、このオブジェクトを取得します。 使用しての詳細については、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>にデータをプロジェクト項目に関連付けるプロパティを参照してください[SharePoint ツール拡張機能とカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)です。  
  
 プロパティの値に変更を保持する、**設定**アクセサーを`ExampleProperty`に新しい値を保存、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>プロパティに関連付けられているオブジェクト。 使用しての詳細については、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>プロジェクト項目では、データを保持するプロパティを参照してください[SharePoint プロジェクト システムの拡張機能でのデータの保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)です。  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>カスタム プロパティの動作を指定します。  
 カスタム プロパティの表示し、では動作を定義することができます、**プロパティ**ウィンドウからの属性を適用することによって、<xref:System.ComponentModel>プロパティ定義の名前空間。 次の属性は、多くのシナリオで役立ちます。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: に表示されるプロパティの名前を指定する、**プロパティ**ウィンドウです。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: の下に表示される説明文字列を指定する、**プロパティ**プロパティが選択されているときにウィンドウです。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: プロパティの既定値を指定します。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: に表示される文字列の間でカスタム変換を指定して、**プロパティ**ウィンドウと非文字列プロパティの値。  
  
-   <xref:System.ComponentModel.EditorAttribute>: を使用して、プロパティを変更するカスタム エディターを指定します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 これらの例では、次のアセンブリへの参照を含むクラス ライブラリ プロジェクトが必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>拡張機能の配置  
 拡張機能を展開するには、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: SharePoint プロジェクト項目の拡張機能を作成します。](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [方法: SharePoint プロジェクト項目の拡張機能にショートカット メニュー項目を追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [SharePoint プロジェクト項目の拡張](../sharepoint/extending-sharepoint-project-items.md)   
 [チュートリアル: SharePoint プロジェクト項目の種類の拡張](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  