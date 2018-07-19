---
title: 'チュートリアル: プロジェクト テンプレートを使用したサイト列プロジェクト項目の作成、パート 1 |Microsoft Docs'
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
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3d34c03d74aae6ba1fb82e7357b6159b261cc2ad
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119535"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>チュートリアル: プロジェクト テンプレート、第 1 部でのサイト列プロジェクト項目を作成します。
  SharePoint プロジェクトは、1 つ以上の SharePoint プロジェクト項目のコンテナーです。 独自の SharePoint プロジェクト項目の種類を作成し、それらをプロジェクト テンプレートと関連付けることで、Visual Studio で SharePoint プロジェクト システムを拡張できます。 このチュートリアルでは、サイト内の列を作成するためのプロジェクト項目の種類を定義し、サイト内の列プロジェクト項目が含まれる新しいプロジェクトの作成に使用できるプロジェクト テンプレートを作成します。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   サイト内の列のための SharePoint プロジェクト項目の新しい種類を定義する Visual Studio 拡張機能の作成。 プロジェクト項目の種類に表示される簡単なカスタム プロパティが含まれています、**プロパティ**ウィンドウ。  
  
-   対応するプロジェクト項目用の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクト テンプレートを作成する。  
  
-   プロジェクト テンプレートおよび拡張機能アセンブリを配置するための [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension (VSIX) パッケージを作成する。  
  
-   プロジェクト項目のデバッグとテストを行う。  
  
 これは、独立したチュートリアルです。 このチュートリアルを完了すると、プロジェクト テンプレートにウィザードを追加してプロジェクト項目を拡張できるようになります。 詳細については、次を参照してください。[チュートリアル: プロジェクト テンプレート、第 2 部でサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)します。  
  
> [!NOTE]  
> 一連のサンプル ワークフローは、次を参照してください。 [SharePoint workflow のサンプル](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples)します。  
  
## <a name="prerequisites"></a>前提条件  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)します。  
  
-   [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 このチュートリアルでは、 **VSIX プロジェクト**sdk プロジェクト アイテムを配置するための VSIX パッケージを作成するテンプレート。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールを拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)します。  
  
 次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   SharePoint のサイト内の列。 詳細については、次を参照してください。[列](http://go.microsoft.com/fwlink/?LinkId=183547)します。  
  
-   Visual Studio のプロジェクト テンプレート。 詳細については、「[Creating Project and Item Templates](/visualstudio/ide/creating-project-and-item-templates)」 (プロジェクトと項目テンプレートの作成) をご覧ください。  
  
## <a name="create-the-projects"></a>プロジェクトを作成します。
 このチュートリアルを実行するには、3 つのプロジェクトを作成する必要があります。  
  
-   VSIX プロジェクト。 このプロジェクトは、サイト内の列プロジェクト項目とプロジェクト テンプレートを配置するための VSIX パッケージを作成します。  
  
-   プロジェクト テンプレート プロジェクト。 このプロジェクトは、サイト内の列プロジェクト項目が含まれる新しい SharePoint プロジェクトを作成するために使用できるプロジェクト テンプレートを作成します。  
  
-   クラス ライブラリ プロジェクト。 このプロジェクトは、サイト内の列プロジェクト項目の動作を定義する Visual Studio 拡張機能を実装します。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### <a name="to-create-the-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。  
  
3.  上部にある、**新しいプロジェクト** ダイアログ ボックスで、ことを確認します **.NET Framework 4.5** .NET Framework のバージョンの一覧でを選択します。  
  
4.  展開、 **Visual Basic**または**Visual c#** ノードを選択し、 **Extensibility**ノード。  
  
    > [!NOTE]  
    >  **Extensibility**ノードは、Visual Studio SDK をインストールする場合にのみ使用できます。 詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
5.  プロジェクト テンプレートの一覧で選択**VSIX プロジェクト**します。  
  
6.  **名前**ボックスに、入力**SiteColumnProjectItem**、選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **SiteColumnProjectItem**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
#### <a name="to-create-the-project-template-project"></a>プロジェクト テンプレート プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ソリューション ノードのショートカット メニューを開き、**追加**を選び、**新しいプロジェクト**します。  
  
2.  上部にある、**新しいプロジェクト** ダイアログ ボックスで、ことを確認します **.NET Framework 4.5** .NET Framework のバージョンの一覧でを選択します。  
  
3.  展開、 **Visual c#** または**Visual Basic**ノードを選択し、**拡張**ノード。  
  
4.  プロジェクト テンプレートの一覧で選択、 **c# プロジェクト テンプレート**または**Visual Basic プロジェクト テンプレート**テンプレート。  
  
5.  **名前**ボックスに、入力**SiteColumnProjectTemplate**、選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **SiteColumnProjectTemplate**プロジェクトがソリューションにします。  
  
6.  Class1 コード ファイルをプロジェクトから削除します。  
  
7.  Visual Basic プロジェクトを作成した場合は、次のファイルもプロジェクトから削除します。  
  
    -   *MyApplication.Designer.vb*  
  
    -   MyApplication.myapp  
  
    -   *Resources.Designer.vb*  
  
    -   *Resources.resx*  
  
    -   *Settings.Designer.vb*  
  
    -   Settings.settings  
  
#### <a name="to-create-the-extension-project"></a>拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ソリューション ノードのショートカット メニューを開き、**追加**を選び、**新しいプロジェクト**します。  
  
2.  上部にある、**新しいプロジェクト** ダイアログ ボックスで、ことを確認します **.NET Framework 4.5** .NET Framework のバージョンの一覧でを選択します。  
  
3.  展開、 **Visual c#** または**Visual Basic** 、ノードの選択、 **Windows**ノードを選択し、**クラス ライブラリ**テンプレート。  
  
4.  **名前**ボックスに、入力**ProjectItemTypeDefinition**選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **ProjectItemTypeDefinition**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
## <a name="configure-the-extension-project"></a>拡張機能プロジェクトを構成します。
 コード ファイルおよびアセンブリ参照を追加し、拡張機能プロジェクトを構成します。  
  
#### <a name="to-configure-the-project"></a>プロジェクトを構成するには  
  
1.  ProjectItemTypeDefinition プロジェクトでは、というコード ファイルを追加**SiteColumnProjectItemTypeProvider**します。  
  
2.  メニュー バーで、**プロジェクト** > **参照の追加**します。  
  
3.  **参照マネージャー - ProjectItemTypeDefinition**  ダイアログ ボックスで、展開、**アセンブリ**ノードを選択、 **Framework**ノード、および選択し、System.componentmodel.composition チェック ボックス。  
  
4.  選択、**拡張機能**ノードが、Microsoft.VisualStudio.SharePoint アセンブリの横にあるチェック ボックスを選択し、、 **OK**ボタン。  
  
## <a name="define-the-new-sharepoint-project-item-type"></a>新しい SharePoint プロジェクト項目の種類を定義します。
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> インターフェイスを実装するクラスを作成して、新しいプロジェクト項目の種類の動作を定義します。 このインターフェイスは、新しい種類のプロジェクト項目を定義するたびに必ず実装します。  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>新しい SharePoint プロジェクト項目の種類を定義するには  
  
1.  **SiteColumnProjectItemTypeProvider**コード ファイル、既定のコードを次のコードに置き換えます、ファイルを保存します。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## <a name="create-a-visual-studio-project-template"></a>Visual Studio プロジェクト テンプレートを作成します。
 プロジェクト テンプレートを作成することにより、サイト内の列プロジェクト項目が含まれる SharePoint プロジェクトを他の開発者が作成できるようになります。 SharePoint プロジェクト テンプレートにはなど、Visual Studio のすべてのプロジェクトに必要なファイルが含まれています *.csproj*または *.vbproj*と *.vstemplate*ファイル、およびファイルSharePoint プロジェクトに固有です。 詳細については、次を参照してください。[項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成する](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)します。  
  
 この手順では、SharePoint プロジェクトに固有のファイルを生成する空の SharePoint プロジェクトを作成します。 次に、これらのファイルが SiteColumnProjectTemplate プロジェクトから生成されるテンプレートに含まれるように、このプロジェクトに追加します。 プロジェクト テンプレートを表示する場所を指定する SiteColumnProjectTemplate プロジェクト ファイルを構成することも、**新しいプロジェクト** ダイアログ ボックス。  
  
#### <a name="to-create-the-files-for-the-project-template"></a>プロジェクト テンプレートのファイルを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の 2 つ目のインスタンスを管理者の資格情報で起動します。  
  
2.  という名前の SharePoint 2010 プロジェクトを作成する**BaseSharePointProject**します。  
  
    > [!IMPORTANT]  
    >  **SharePoint カスタマイズ ウィザード**、選択しないでください、**ファーム ソリューションとして配置**オプション ボタンをクリックします。  
  
3.  プロジェクトに空の要素項目を追加し、名前を項目**Field1**します。  
  
4.  プロジェクトを保存し、2 つ目の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] インスタンスを閉じます。  
  
5.  インスタンスで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で SiteColumnProjectItem ソリューションを開いてを持つ**ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SiteColumnProjectTemplate** でプロジェクトノード、**追加**を選び、**既存項目の**します。  
  
6.  **既存項目の追加**ダイアログ ボックスで、ファイル拡張機能の一覧を表示し、**すべてのファイル (\*.\*)**.  
  
7.  BaseSharePointProject プロジェクトが含まれる、ディレクトリで、key.snk ファイルを選択し、**追加**ボタンをクリックします。  
  
    > [!NOTE]  
    >  このチュートリアルで作成するプロジェクト テンプレートでは、テンプレートを使用して作成される各プロジェクトに署名するために、同じ key.snk ファイルが使用されます。 プロジェクト インスタンスごとに別の key.snk ファイルを作成するには、このサンプルを拡張する方法については、次を参照してください。[チュートリアル: プロジェクト テンプレート、第 2 部でサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)します。  
  
8.  手順 5. ～ 8. を繰り返して、BaseSharePointProject ディレクトリの指定されているサブフォルダーから次のファイルを追加します。  
  
    -   *\Field1\Elements.xml*  
  
    -   *\Field1\SharePointProjectItem.spdata*  
  
    -   *\Features\Feature1\Feature1.feature*  
  
    -   *\Features\Feature1\Feature1.Template.xml*  
  
    -   *\Package\Package.package*  
  
    -   *\Package\Package.Template.xml*  
  
     これらのファイルは SiteColumnProjectTemplate プロジェクトに直接追加します。プロジェクト内に Field1、Features、または Package の各サブフォルダーを再作成しないでください。 これらのファイルの詳細については、次を参照してください。[項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成する](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)します。  
  
#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>[新しいプロジェクト] ダイアログ ボックスでのプロジェクト テンプレートの表示方法を構成するには
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SiteColumnProjectTemplate**プロジェクト ノードを選び、**プロジェクトのアンロード**します。 すべてのファイルに対する変更を保存する場合は、選択、**はい**ボタンをクリックします。  
  
2.  ショートカット メニューを開き、 **SiteColumnProjectTemplate**ノード、もう一度クリックして**sitecolumnprojecttemplate.csproj の編集**または**sitecolumnprojecttemplate.vbproj の編集**.  
  
3.  プロジェクト ファイル内で、次の `VSTemplate` 要素を見つけます。  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  この要素を次の XML に置き換えます。  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` 要素は、プロジェクトをビルドするとプロジェクト テンプレートが作成されるパス内の追加フォルダーを指定します。 ここで指定したフォルダーは、顧客を開く場合にのみ、プロジェクト テンプレートが利用できるということを確認、**新しいプロジェクト** ダイアログ ボックスで、展開、 **SharePoint**ノードを選択し、 **2010**ノード。  
  
5.  ファイルを保存して閉じます。  
  
6.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SiteColumnProjectTemplate**プロジェクトを選び、**プロジェクトの再読み込み**します。  
  
## <a name="edit-the-project-template-files"></a>プロジェクトのテンプレート ファイルを編集します。
 SiteColumnProjectTemplate プロジェクトで次のファイルを編集して、プロジェクト テンプレートの動作を定義します。  
  
-   *AssemblyInfo.cs*または*AssemblyInfo.vb*  
  
-   *Elements.xml*  
  
-   *SharePointProjectItem.spdata*  
  
-   *Feature1.feature*  
  
-   *Package.package*  
  
-   *SiteColumnProjectTemplate.vstemplate*  
  
-   *ProjectTemplate.csproj*または*ProjectTemplate.vbproj*  
  
 次の手順では、これらのファイルのいくつかに置き換え可能パラメーターを追加します。 置き換え可能パラメーターはトークンであり、先頭と末尾にはドル記号 ($) が付いています。 ユーザーがこのプロジェクト テンプレートを使用してプロジェクトを作成するときに、Visual Studio によって自動的に新しいプロジェクト内のこれらのパラメーターが特定の値で置き換えられます。 詳細については、次を参照してください。[置き換え可能パラメーター](../sharepoint/replaceable-parameters.md)します。  
  
#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>AssemblyInfo.cs ファイルまたは AssemblyInfo.vb ファイルを編集するには
  
1.  SiteColumnProjectTemplate プロジェクトで開き、 *AssemblyInfo.cs*または*AssemblyInfo.vb*ファイルを開き、上部に、次のステートメントを追加します。  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     ときに、**サンド ボックス ソリューション**SharePoint プロジェクトのプロパティに設定されて**True**、Visual Studio の追加、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> AssemblyInfo コード ファイルにします。 ただし、プロジェクト テンプレートの AssemblyInfo コード ファイルは、既定では <xref:System.Security> 名前空間をインポートしません。 これを追加する必要があります**を使用して**または**Imports**を防ぐためにステートメントのコンパイル エラーが発生します。  
  
2.  ファイルを保存して閉じます。  
  
#### <a name="to-edit-the-elementsxml-file"></a>Elements.xml ファイルを編集するには
  
1.  SiteColumnProjectTemplate プロジェクトでの内容を置き換える、 *Elements.xml*を次の XML ファイル。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     新しい XML により、サイト内の列の名前、その基本型、およびギャラリーでサイト内の列が表示されるグループを定義する `Field` 要素が追加されます。 このファイルの内容に関する詳細については、次を参照してください。[フィールド定義スキーマ](http://go.microsoft.com/fwlink/?LinkId=184290)します。  
  
2.  ファイルを保存して閉じます。  
  
#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>SharePointProjectItem.spdata ファイルを編集するには
  
1.  SiteColumnProjectTemplate プロジェクトでの内容を置き換える、 *SharePointProjectItem.spdata*を次の XML ファイル。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                 xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
      </Files>   
    </ProjectItem>  
    ```  
  
     新しい XML により、ファイルは次のように変更されます。  
  
    -   `Type` 要素の `ProjectItem` 属性は、プロジェクト項目定義 (先ほど作成した <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> クラス) の `SiteColumnProjectItemTypeProvider` に渡すものと同じ文字列に変更されます。  
  
    -   `SupportedTrustLevels` 属性と `SupportedDeploymentScopes` 属性が `ProjectItem` 要素から削除されます。 信頼レベルと配置のスコープは ProjectItemTypeDefinition プロジェクトの `SiteColumnProjectItemTypeProvider` クラスに指定されているため、これらの属性値は不要です。  
  
     内容の詳細については *.spdata*ファイルを参照してください[SharePoint プロジェクト項目スキーマのリファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)します。  
  
2.  ファイルを保存して閉じます。  
  
#### <a name="to-edit-the-feature1feature-file"></a>Feature1.feature ファイルを編集するには
  
1.  SiteColumnProjectTemplate プロジェクトでの内容を置き換える、 *Feature1.feature*を次の XML ファイル。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
             imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
             deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
      <projectItems>  
        <projectItemReference itemId="$guid2$" />  
      </projectItems>  
    </feature>  
    ```  
  
     新しい XML により、ファイルは次のように変更されます。  
  
    -   `Id` 要素の `featureId` 属性と `feature` 属性の値が `$guid4$` に変更されます。  
  
    -   `itemId` 要素の `projectItemReference` 属性の値が `$guid2$` に変更されます。  
  
     詳細については *.feature*ファイルを参照してください[項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成する](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)します。  
  
2.  ファイルを保存して閉じます。  
  
#### <a name="to-edit-the-packagepackage-file"></a>Package.package ファイルを編集するには
  
1.  SiteColumnProjectTemplate プロジェクトでの内容を置き換える、 *Package.package*を次の XML ファイル。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
             Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
      <features>  
        <featureReference itemId="$guid4$" />  
      </features>  
    </package>  
    ```  
  
     新しい XML により、ファイルは次のように変更されます。  
  
    -   `Id` 要素の `solutionId` 属性と `package` 属性の値が `$guid3$` に変更されます。  
  
    -   `itemId` 要素の `featureReference` 属性の値が `$guid4$` に変更されます。  
  
     詳細については *.package*ファイルを参照してください[項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成する](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)します。  
  
2.  ファイルを保存して閉じます。  
  
#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Sitecolumnprojecttemplate.vstemplate ファイルを編集するには
  
1.  SiteColumnProjectTemplate プロジェクトで、SiteColumnProjectTemplate.vstemplate ファイルの内容を、次に示す XML セクションのいずれかと置き換えます。  
  
    -   Visual C# プロジェクト テンプレートを作成している場合は、次の XML を使用します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>CSharp</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
    -   Visual Basic プロジェクト テンプレートを作成している場合は、次の XML を使用します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>VisualBasic</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     新しい XML により、ファイルは次のように変更されます。  
  
    -   セット、`Name`要素の値に**Site Column**します。 (この名前に表示されます、**新しいプロジェクト** ダイアログ ボックス)。  
  
    -   各プロジェクト インスタンスに含まれているファイルごとに、`ProjectItem` 要素が追加されます。  
  
    -   名前空間を使用"http://schemas.microsoft.com/developer/vstemplate/2005"。 このソリューションの使用法の場合は、他のプロジェクト ファイル、"http://schemas.microsoft.com/developer/msbuild/2003"名前空間。 このため、XML スキーマ警告メッセージが生成されますが、このチュートリアルでは、これらを無視できます。  
  
     内容の詳細については *.vstemplate*ファイルを参照してください[Visual Studio テンプレート スキーマ参照](/visualstudio/extensibility/visual-studio-template-schema-reference)します。  
  
2.  ファイルを保存して閉じます。  
  
#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Projecttemplate.csproj または projecttemplate.vbproj ファイルを編集するには
  
1.  SiteColumnProjectTemplate プロジェクトでの内容を置き換える、 *ProjectTemplate.csproj*ファイルまたは*ProjectTemplate.vbproj* XML の次のセクションのいずれかのファイル。  
  
    -   Visual C# プロジェクト テンプレートを作成している場合は、次の XML を使用します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  Visual Basic プロジェクト テンプレートを作成している場合は、次の XML を使用します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     新しい XML により、ファイルは次のように変更されます。  
  
    -   `TargetFrameworkVersion` 要素を使用して、.NET Framework 3.5 (4.5 ではない) が指定されます。  
  
    -   プロジェクトの出力に署名するための `SignAssembly` 要素と `AssemblyOriginatorKeyFile` 要素が追加されます。  
  
    -   SharePoint プロジェクトによって使用されるアセンブリ参照用の `Reference` 要素が追加されます。  
  
    -   など、プロジェクトで、既定のファイルごとの要素を追加*Elements.xml*と*SharePointProjectItem.spdata*します。  
  
2.  ファイルを保存して閉じます。  
  
## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>プロジェクト テンプレートをデプロイする VSIX パッケージを作成します。
 拡張機能を展開するで、VSIX プロジェクトを使用、 **SiteColumnProjectItem** VSIX パッケージを作成するソリューションです。 まず、VSIX プロジェクトに含まれている source.extension.vsixmanifest ファイルを変更して、VSIX パッケージを構成します。 次に、ソリューションをビルドして VSIX パッケージを作成します。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX パッケージを構成および作成するには  
  
1.  **ソリューション エクスプ ローラー**の**SiteColumnProjectItem**プロジェクトで、マニフェスト エディターで source.extension.vsixmanifest ファイルを開きます。  
  
     source.extension.vsixmanifest ファイルが、すべての VSIX パッケージで必要になる extension.vsixmanifest ファイルの基礎となります。 このファイルの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)します。  
  
2.  **製品名**ボックスに、入力**Site Column**します。  
  
3.  **作成者**ボックスに、入力**Contoso**します。  
  
4.  **説明**ボックスに、入力**サイト内の列を作成するための A SharePoint project**します。  
  
5.  選択、**資産**、タブをクリックして、**新規**ボタンをクリックします。  
  
     **新しい資産の追加** ダイアログ ボックスが表示されます。  
  
6.  **型**一覧で、選択**Microsoft.VisualStudio.ProjectTemplate**します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `ProjectTemplate` 要素に対応します。 この要素は、プロジェクト テンプレートを格納する VSIX パッケージ内のサブフォルダーを示します。 詳細については、次を参照してください。 [ProjectTemplate 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1)します。  
  
7.  **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。  
  
8.  **プロジェクト**一覧を**SiteColumnProjectTemplate**、選択し、 **OK**ボタン。  
  
9. 選択、**新規**もう一度ボタンをクリックします。  
  
     **新しい資産の追加** ダイアログ ボックスが表示されます。  
  
10. **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。 この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)します。  
  
11. **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。  
  
12. **プロジェクト**一覧で、選択**ProjectItemTypeDefinition**、選択し、 **OK**ボタン。  
  
13. メニュー バーで、**ビルド** > **ソリューションのビルド**のエラーのないプロジェクトをコンパイルできるかどうかを確認します。  
  
## <a name="test-the-project-template"></a>テスト プロジェクト テンプレート
 これで、プロジェクト テンプレートをテストする準備ができました。 まず、Visual Studio の実験用インスタンスで SiteColumnProjectItem ソリューションのデバッグを開始します。 次に、テスト、 **Site Column** Visual Studio の実験用インスタンスでのプロジェクト。 最後に、SharePoint プロジェクトをビルドして実行し、サイト内の列が正常に機能することを確認します。  
  
#### <a name="to-start-debugging-the-solution"></a>ソリューションのデバッグを開始するには  
  
1.  管理者の資格情報で Visual Studio を再起動し、SiteColumnProjectItem ソリューションを開きます。  
  
2.  
  
3.  SiteColumnProjectItemTypeProvider コード ファイルでは、コード内の最初の行にブレークポイントを追加、`InitializeType`メソッドを選択し、 **F5**デバッグを開始するキー。  
  
     Visual Studio によって、拡張機能が %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 にインストールされ、Visual Studio の実験用インスタンスが開始されます。 このインスタンスの Visual Studio でプロジェクト項目をテストします。  
  
#### <a name="to-test-the-project-in-visual-studio"></a>Visual Studio でプロジェクトをテストするには  
  
1.  メニュー バーで、Visual Studio の実験用インスタンスで次のように選択します。**ファイル** > **新規** > **プロジェクト**します。  
  
2.  展開、 **Visual c#** または**Visual Basic** (言語に応じて、プロジェクト テンプレートがサポートする)、ノードを展開、 **SharePoint**ノード、を選択し、**2010**ノード。  
  
3.  プロジェクト テンプレートの一覧で選択、 **Site Column**テンプレート。  
  
4.  **名前**ボックスに、入力**SiteColumnTest**選択し、 **OK**ボタン。  
  
     **ソリューション エクスプ ローラー**、新しいプロジェクトというプロジェクト項目に表示されます**Field1**します。  
  
5.  Visual Studio の他のインスタンス内のコードを以前に設定したブレークポイントで停止することを確認、`InitializeType`メソッドを選択し、 **F5**プロジェクトのデバッグを続行するキー。  
  
6.  **ソリューション エクスプ ローラー**、選択、 **Field1**ノードを選択し、 **F4**キー。  
  
     **プロパティ**ウィンドウが開きます。  
  
7.  プロパティ ボックスの一覧であることを確認プロパティ**プロパティの例**が表示されます。  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>SharePoint でサイト内の列をテストするには  
  
1.  **ソリューション エクスプ ローラー**、選択、 **SiteColumnTest**ノード。  
  
2.  **プロパティ**ウィンドウの横にあるテキスト ボックスで、**サイトの URL**プロパティ、入力 **http://localhost**します。  
  
     この手順により、デバッグに使用する開発用コンピューター上のローカル SharePoint サイトが指定されます。  
  
    > [!NOTE]  
    >  **サイトの URL** Site Column プロジェクト テンプレートは、プロジェクトが作成されるときに、この値を収集するため、ウィザードを提供しないために、プロパティが既定では空です。 この値を開発者を要求し、新しいプロジェクトでこのプロパティを構成するウィザードを追加する方法については、次を参照してください。[チュートリアル: プロジェクト テンプレート、第 2 部でサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)します。  
  
3.  **F5** キーを押します。  
  
     サイト内の列がパッケージ化されで指定されている SharePoint サイトに配置された、**サイトの URL**プロジェクトのプロパティ。 Web ブラウザーには、このサイトの既定のページが表示されます。  
  
    > [!NOTE]  
    >  場合、**スクリプト デバッグが無効**選択 ダイアログ ボックスが表示されたら、**はい**クリックしてプロジェクトのデバッグを続行します。  
  
4.  **サイトの操作**] メニューの [選択**サイト設定**します。  
  
5.  **サイト設定**ページの**ギャラリー**一覧で、選択、**サイト列**リンク。  
  
6.  サイト内の列の一覧であることを確認、 **Custom Columns**グループにはという列が含まれています**SiteColumnTest**します。  
  
7.  Web ブラウザーを閉じます。  
  
## <a name="clean-up-the-development-computer"></a>開発用コンピューターをクリーンアップします。
 プロジェクトのテストが終わったら、プロジェクト テンプレートを Visual Studio の実験用インスタンスから削除します。  
  
#### <a name="to-clean-up-the-development-computer"></a>開発コンピューターをクリーンアップするには  
  
1.  メニュー バーで、Visual Studio の実験用インスタンスで次のように選択します。**ツール** > **拡張機能と更新**します。  
  
     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で選択、**サイト内の列**拡張機能を選択し、**アンインストール**ボタンをクリックします。  
  
3.  ダイアログ ボックスが表示されますが、選択、**はい**ボタン拡張機能をアンインストールすることを確認します。  
  
4.  選択、**閉じる**アンインストールを完了するボタンをクリックします。  
  
5.  Visual Studio の両方のインスタンス (実験用インスタンスと SiteColumnProjectItem ソリューションを開いたインスタンス) を閉じます。  
  
## <a name="next-steps"></a>次の手順
 このチュートリアルを完了すると、プロジェクト テンプレートにウィザードを追加できるようになります。 ユーザーが Site Column プロジェクトを作成するときに、ウィザードが、デバッグに使用するサイトの URL と、新しいソリューションがサンドボックス ソリューションかどうかをユーザーに尋ね、この情報を使用して新しいプロジェクトを構成します。 ウィザードも (基本データ型をサイト列ギャラリー内の列を一覧表示するグループなど) の列に関する情報を収集し、この情報を追加します、 *Elements.xml*で新しいプロジェクト ファイル。 詳細については、次を参照してください。[チュートリアル: プロジェクト テンプレート、第 2 部でサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)します。  
  
## <a name="see-also"></a>関連項目
 [チュートリアル: プロジェクト テンプレート、第 2 部でのサイト列プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成します。](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [SharePoint プロジェクト システムの拡張機能でデータを保存します。](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [SharePoint ツール拡張機能とカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
