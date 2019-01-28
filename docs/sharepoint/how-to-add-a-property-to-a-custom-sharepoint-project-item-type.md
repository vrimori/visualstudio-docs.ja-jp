---
title: '方法: カスタム SharePoint プロジェクト項目の種類のプロパティの追加 |Microsoft Docs'
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
ms.openlocfilehash: ca3bfbf6ecd773f0a7c3147a44eb02a5c260764b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872795"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>方法: カスタム SharePoint プロジェクト項目の種類にプロパティを追加します。
  カスタム SharePoint プロジェクト項目の種類を定義するときに、プロジェクト項目にプロパティを追加できます。 プロパティを表示する、**プロパティ**ウィンドウで、プロジェクト項目を選択すると**ソリューション エクスプ ローラー**します。  
  
 次の手順では、独自の SharePoint プロジェクト項目の種類が既に定義されている前提としています。 詳細については、「[方法 :SharePoint プロジェクト項目の種類定義](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)します。  
  
### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>プロジェクト項目の種類の定義にプロパティを追加するには  
  
1.  カスタム プロジェクト項目の種類を追加するプロパティを表すパブリック プロパティを持つクラスを定義します。 カスタム プロジェクト項目の種類に複数のプロパティを追加する場合は、同じクラスまたは別のクラスですべてのプロパティを定義できます。  
  
2.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>のメソッド、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>実装、ハンドル、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>のイベント、 *projectItemTypeDefinition*パラメーター。  
  
3.  イベント ハンドラーで、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>イベントには、カスタム プロパティ クラスのインスタンスを追加、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A>イベント引数のパラメーターのコレクション。  
  
## <a name="example"></a>例  
 次のコード例は、という名前のプロパティを追加する方法を示します**プロパティの例**カスタム プロジェクト項目の種類。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]  
  
### <a name="understand-the-code"></a>コードを理解します。  
 同じインスタンスを確実に、`CustomProperties`クラスには、毎回、使用、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>イベントが発生した、コード例にプロパティ オブジェクトの保存、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>プロジェクト最初の項目にこのイベントが発生するプロパティ。 コードは、このイベントが発生するたびに、このオブジェクトを取得します。 使用しての詳細については、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>プロジェクトの項目を含むデータを保存するプロパティを参照してください[ツールの拡張機能を SharePoint でカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)します。  
  
 プロパティの値に変更を保持する、**設定**のアクセサー`ExampleProperty`に新しい値を保存、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>プロパティが関連付けられているオブジェクト。 使用しての詳細については、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>プロジェクトの項目を含むデータを保持するプロパティを参照してください[SharePoint プロジェクト システムの拡張機能でデータを保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)します。  
  
### <a name="specify-the-behavior-of-custom-properties"></a>カスタム プロパティの動作を指定します。  
 カスタム プロパティの表示し、動作を定義することができます、**プロパティ**ウィンドウからの属性を適用することで、<xref:System.ComponentModel>プロパティ定義に名前空間。 次の属性には、多くのシナリオがあります。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>:表示されるプロパティの名前を指定します、**プロパティ**ウィンドウ。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>:下に表示される説明文字列を指定します、**プロパティ**プロパティが選択されている場合は、ウィンドウ。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>:プロパティの既定値を指定します。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>:カスタムの変換との間に表示される文字列を指定します、**プロパティ**ウィンドウと非文字列プロパティの値。  
  
-   <xref:System.ComponentModel.EditorAttribute>:使用して、プロパティを変更するカスタム エディターを指定します。  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 これらのコード例では、次のアセンブリへの参照を含むクラス ライブラリ プロジェクトが必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>プロジェクト項目を配置します。  
 他の開発者が自分のプロジェクト項目を有効にするには、プロジェクト テンプレートまたはプロジェクト項目テンプレートを作成します。 詳細については、次を参照してください。[項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成する](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)します。  
  
 プロジェクト項目を展開するには、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]拡張機能 (VSIX) に、アセンブリ、テンプレート、およびその他のファイル プロジェクト項目に配布するパッケージ化します。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [方法: SharePoint プロジェクト項目の種類を定義します。](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [方法: カスタム SharePoint プロジェクト項目の種類のショートカット メニュー項目を追加します。](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
