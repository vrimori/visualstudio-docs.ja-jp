---
title: '方法: SharePoint プロジェクトにプロパティを追加 |Microsoft Docs'
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
ms.openlocfilehash: 015725197c2c269a7b6aed2e20f0159e2a9f2fe6
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758560"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>方法: SharePoint プロジェクトにプロパティを追加
  プロジェクトの拡張機能を使用すると、任意の SharePoint プロジェクトにプロパティを追加します。 プロパティを表示する、**プロパティ**ウィンドウで、プロジェクトを選択すると**ソリューション エクスプ ローラー**します。  
  
 次の手順では、プロジェクトの拡張機能を既に作成したことを前提としています。 詳細については、次を参照してください。[方法: SharePoint プロジェクト拡張機能作成](../sharepoint/how-to-create-a-sharepoint-project-extension.md)です。  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>SharePoint プロジェクトにプロパティを追加するには  
  
1.  SharePoint プロジェクトに追加するプロパティを表すパブリック プロパティを持つクラスを定義します。 複数のプロパティを追加する場合は、同じクラスまたは別のクラスですべてのプロパティを定義できます。  
  
2.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>のメソッド、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>実装、ハンドル、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>のイベント、 *projectService*パラメーター。  
  
3.  イベント ハンドラーで、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>イベント、プロパティ、クラスのインスタンスを追加、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A>イベント引数のパラメーターのコレクション。  
  
## <a name="example"></a>例  
 次のコード例では、SharePoint プロジェクトに 2 つのプロパティを追加する方法を示します。 1 つのプロパティが、プロジェクト ユーザー オプション ファイル内のデータを永続化 (、 *. csproj.user*ファイルまたは *. vbproj.user*ファイル)。 その他のプロパティは、プロジェクト ファイル内のデータを永続化 (*.csproj*ファイルまたは *.vbproj*ファイル)。  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understand-the-code"></a>コードを理解します。  
 同じインスタンスを確実に、`CustomProjectProperties`クラスには、毎回、使用、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>イベントが発生する、プロパティ オブジェクトを追加するコード例、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>最初のプロジェクトにこのイベントが発生するプロパティ。 コードは、このイベントが発生するたびに、このオブジェクトを取得します。 使用しての詳細については、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>プロジェクトでは、データを関連付けるプロパティを参照してください[ツールの拡張機能を SharePoint でカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)します。  
  
 プロパティの値に変更を保持する、**設定**プロパティのアクセサーは、次の Api を使用します。  
  
-   `CustomUserFileProperty` 使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A>プロジェクト ユーザー オプション ファイルにその値を保存するプロパティ。  
  
-   `CustomProjectFileProperty` 使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>その値をプロジェクト ファイルに保存するメソッド。  
  
 これらのファイルでデータの永続化の詳細については、次を参照してください。 [SharePoint プロジェクト システムの拡張機能でデータを保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)します。  
  
### <a name="specify-the-behavior-of-custom-properties"></a>カスタム プロパティの動作を指定します。  
 カスタム プロパティの表示し、動作を定義することができます、**プロパティ**ウィンドウからの属性を適用することで、<xref:System.ComponentModel>プロパティ定義に名前空間。 次の属性には、多くのシナリオがあります。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: に表示されるプロパティの名前を指定します、**プロパティ**ウィンドウ。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: の下部に表示される説明文字列を指定します、**プロパティ**、プロパティが選択されている場合は、ウィンドウ。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: プロパティの既定値を指定します。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: カスタムの変換との間に表示される文字列を指定します、**プロパティ**ウィンドウと非文字列プロパティの値。  
  
-   <xref:System.ComponentModel.EditorAttribute>: 使用して、プロパティを変更するカスタム エディターを指定します。  
  
## <a name="compile-the-code"></a>コードをコンパイルします  
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
  
## <a name="deploy-the-extension"></a>拡張機能をデプロイします。  
 拡張機能を展開するには、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクトを拡張します。](../sharepoint/extending-sharepoint-projects.md)   
 [方法: SharePoint プロジェクト拡張機能の作成](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [方法: SharePoint プロジェクトのショートカット メニュー項目の追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [SharePoint プロジェクト システムを拡張します。](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
