---
title: '方法: カスタム SharePoint プロジェクト項目の種類にプロパティを追加 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7270ee0171d5ed7df94ab186e22e1bc82b7d93c2
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767547"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>方法: カスタム SharePoint プロジェクト項目の種類にプロパティを追加
  カスタム SharePoint プロジェクト項目の種類を定義するときは、プロジェクト項目に、プロパティを追加することができます。 このプロパティを表示、**プロパティ**ウィンドウで、プロジェクト項目を選択すると**ソリューション エクスプ ローラー**です。  
  
 次の手順では、独自の SharePoint プロジェクト項目の種類が既に定義されていると仮定します。 詳細については、次を参照してください。[する方法: SharePoint プロジェクト項目の種類を定義する](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)です。  
  
### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>プロジェクト項目の種類の定義にプロパティを追加するには  
  
1.  カスタム プロジェクト項目の種類を追加するプロパティを表すパブリック プロパティを持つクラスを定義します。 カスタム プロジェクト項目の種類に複数のプロパティを追加する場合は、同じクラスまたは異なるクラスのすべてのプロパティを定義できます。  
  
2.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>のメソッド、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>実装、ハンドル、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>のイベント、 *projectItemTypeDefinition*パラメーター。  
  
3.  イベント ハンドラーで、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>イベントには、カスタム プロパティをクラスのインスタンスを追加、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A>イベント引数のパラメーターのコレクション。  
  
## <a name="example"></a>例  
 次のコード例は、という名前のプロパティを追加する方法を示します**Example Property**をカスタム プロジェクト項目の種類。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]  
  
### <a name="understanding-the-code"></a>コードをについてください。  
 同じインスタンスのことを確認する、`CustomProperties`クラスには、毎回、使用、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>イベントが発生すると、コード例は、プロパティ オブジェクトを保存、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>プロジェクト項目の最初のこのイベントの発生時のプロパティです。 コードは、このイベントが再度発生するたびに、このオブジェクトを取得します。 使用しての詳細については、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>プロジェクト項目では、データを保存するプロパティを参照してください[SharePoint ツール拡張機能とカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)です。  
  
 プロパティの値に変更を保持する、**設定**アクセサーを`ExampleProperty`に新しい値を保存、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>プロパティに関連付けられているオブジェクト。 使用しての詳細については、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>プロジェクト項目では、データを保持するプロパティを参照してください[SharePoint プロジェクト システムの拡張機能でのデータの保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)です。  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>カスタム プロパティの動作を指定します。  
 カスタム プロパティの表示し、では動作を定義することができます、**プロパティ**ウィンドウからの属性を適用することによって、<xref:System.ComponentModel>プロパティ定義の名前空間。 次の属性は、多くのシナリオで役立ちます。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: に表示されるプロパティの名前を指定する、**プロパティ**ウィンドウです。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: の下に表示される説明文字列を指定する、**プロパティ**プロパティが選択されているときにウィンドウです。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: プロパティの既定値を指定します。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: に表示される文字列の間でカスタム変換を指定して、**プロパティ**ウィンドウと非文字列プロパティの値。  
  
-   <xref:System.ComponentModel.EditorAttribute>: を使用して、プロパティを変更するカスタム エディターを指定します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 これらのコード例では、次のアセンブリへの参照を含むクラス ライブラリ プロジェクトが必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>プロジェクト項目の展開  
 プロジェクト項目を使用するには、他の開発者を有効にするには、プロジェクト テンプレートまたはプロジェクト項目テンプレートを作成します。 詳細については、次を参照してください。[項目テンプレートを作成し、SharePoint プロジェクト項目用のプロジェクト テンプレート](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)です。  
  
 プロジェクト項目を展開するには、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]拡張機能 (VSIX) に、アセンブリ、テンプレート、およびその他のファイル プロジェクト項目と共に配布するパッケージ化します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目
 [方法: SharePoint プロジェクト項目の種類の定義](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [方法: カスタム SharePoint プロジェクト項目の種類へのショートカット メニュー項目の追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [SharePoint プロジェクト項目の種類の定義](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  
