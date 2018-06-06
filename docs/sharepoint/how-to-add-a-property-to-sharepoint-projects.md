---
title: '方法: SharePoint プロジェクトにプロパティを追加 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 44e82b15ff2d4bdfaac5e8e9eca672ecdc1780a9
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767622"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>方法: SharePoint プロジェクトにプロパティを追加
  プロジェクトの拡張機能を使用すると、任意の SharePoint プロジェクトにプロパティを追加します。 このプロパティを表示、**プロパティ**ウィンドウで、プロジェクトを選択すると**ソリューション エクスプ ローラー**です。  
  
 次の手順では、プロジェクトの拡張機能が既に作成されたことを前提としています。 詳細については、次を参照してください。[する方法: SharePoint プロジェクトの拡張機能を作成する](../sharepoint/how-to-create-a-sharepoint-project-extension.md)です。  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>SharePoint プロジェクトにプロパティを追加するには  
  
1.  SharePoint プロジェクトに追加するプロパティを表すパブリック プロパティを持つクラスを定義します。 複数のプロパティを追加する場合は、同じクラスまたは異なるクラスのすべてのプロパティを定義できます。  
  
2.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>のメソッド、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>実装、ハンドル、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>のイベント、 *projectService*パラメーター。  
  
3.  イベント ハンドラーで、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>イベント、プロパティ、クラスのインスタンスを追加、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A>イベント引数のパラメーターのコレクション。  
  
## <a name="example"></a>例  
 次のコード例では、SharePoint プロジェクトに 2 つのプロパティを追加する方法を示します。 1 つのプロパティには、プロジェクト ユーザー オプション ファイル内のデータが引き続き発生する (、 *. csproj.user*ファイルまたは *. vbproj.user*ファイル)。 その他のプロパティは、プロジェクト ファイルでそのデータを永続化 (*.csproj*ファイルまたは *.vbproj*ファイル)。  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understanding-the-code"></a>コードをについてください。  
 同じインスタンスのことを確認する、`CustomProjectProperties`クラスには、毎回、使用、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>イベントが発生する、プロパティ オブジェクトを追加するコード例、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>プロジェクト、最初にこのイベントが発生するプロパティです。 コードは、このイベントが再度発生するたびに、このオブジェクトを取得します。 使用しての詳細については、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>にデータを関連付けるプロジェクトでは、プロパティを参照してください[SharePoint ツール拡張機能とカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)です。  
  
 プロパティの値に変更を保持する、**設定**プロパティのアクセサーは、次の Api を使用します。  
  
-   `CustomUserFileProperty` 使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A>プロジェクト ユーザー オプション ファイルにその値を保存するプロパティです。  
  
-   `CustomProjectFileProperty` 使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>プロジェクト ファイルにその値を保存する方法です。  
  
 これらのファイルでデータの永続化の詳細については、次を参照してください。 [SharePoint プロジェクト システムの拡張機能でのデータの保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)です。  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>カスタム プロパティの動作を指定します。  
 カスタム プロパティの表示し、では動作を定義することができます、**プロパティ**ウィンドウからの属性を適用することによって、<xref:System.ComponentModel>プロパティ定義の名前空間。 次の属性は、多くのシナリオで役立ちます。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: に表示されるプロパティの名前を指定する、**プロパティ**ウィンドウです。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: の下に表示される説明文字列を指定する、**プロパティ**プロパティが選択されているときにウィンドウです。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: プロパティの既定値を指定します。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: に表示される文字列の間でカスタム変換を指定して、**プロパティ**ウィンドウと非文字列プロパティの値。  
  
-   <xref:System.ComponentModel.EditorAttribute>: を使用して、プロパティを変更するカスタム エディターを指定します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint
-    
-   Microsoft.VisualStudio.Shell
-     
-   Microsoft.VisualStudio.Shell.Interop
-     
-   Microsoft.VisualStudio.Shell.Interop.8.0
-     
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>拡張機能の配置  
 拡張機能を展開するには、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクトの拡張](../sharepoint/extending-sharepoint-projects.md)   
 [方法: SharePoint プロジェクトの拡張機能を作成します。](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [方法: SharePoint プロジェクトへのショートカット メニュー項目の追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [SharePoint プロジェクト システムの拡張](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
