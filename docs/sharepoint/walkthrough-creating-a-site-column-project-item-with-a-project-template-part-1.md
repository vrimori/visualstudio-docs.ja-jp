---
title: "チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 (パート 1)"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint プロジェクト項目、定義 (独自の型を)"
  - "プロジェクト項目 [Visual Studio での SharePoint 開発]、定義 (独自の型を)"
  - "SharePoint プロジェクト、作成 (カスタム テンプレートを)"
  - "Visual Studio での SharePoint 開発、定義 (新しいプロジェクト項目の種類を)"
ms.assetid: b53d48d7-cbf2-45c2-9537-06a6819be397
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 (パート 1)
  SharePoint プロジェクトは、1 つ以上の SharePoint プロジェクト項目のコンテナーです。  独自の SharePoint プロジェクト項目の種類を作成し、それらをプロジェクト テンプレートと関連付けることで、Visual Studio で SharePoint プロジェクト システムを拡張できます。  このチュートリアルでは、サイト内の列を作成するためのプロジェクト項目の種類を定義し、サイト内の列プロジェクト項目が含まれる新しいプロジェクトの作成に使用できるプロジェクト テンプレートを作成します。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   サイト内の列のための SharePoint プロジェクト項目の新しい種類を定義する Visual Studio 拡張機能の作成。  プロジェクト項目の種類には、**\[プロパティ\]** ウィンドウに表示される単純なカスタム プロパティが含まれます。  
  
-   対応するプロジェクト項目用の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクト テンプレートを作成する。  
  
-   プロジェクト テンプレートおよび拡張機能アセンブリを配置するための [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成する。  
  
-   プロジェクト項目のデバッグとテストを行う。  
  
 これは、独立したチュートリアルです。  このチュートリアルを完了すると、プロジェクト テンプレートにウィザードを追加してプロジェクト項目を拡張できるようになります。  詳細については、「[チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 2&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)」を参照してください。  
  
> [!NOTE]  
>  このチュートリアル用の完全なプロジェクト、コード、およびその他のファイルを含むサンプルは、[http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369) からダウンロードできます。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  このチュートリアルでは、SDK の **VSIX プロジェクト** テンプレートを使用して、プロジェクト項目を配置するための VSIX パッケージを作成します。  詳細については、「[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
 次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   SharePoint のサイト内の列。  詳細については、「[列](http://go.microsoft.com/fwlink/?LinkId=183547)」を参照してください。  
  
-   Visual Studio のプロジェクト テンプレート。  詳細については、「[Visual Studio でのカスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)」を参照してください。  
  
## プロジェクトの作成  
 このチュートリアルを実行するには、3 つのプロジェクトを作成する必要があります。  
  
-   VSIX プロジェクト。  このプロジェクトは、サイト内の列プロジェクト項目とプロジェクト テンプレートを配置するための VSIX パッケージを作成します。  
  
-   プロジェクト テンプレート プロジェクト。  このプロジェクトは、サイト内の列プロジェクト項目が含まれる新しい SharePoint プロジェクトを作成するために使用できるプロジェクト テンプレートを作成します。  
  
-   クラス ライブラリ プロジェクト。  このプロジェクトは、サイト内の列プロジェクト項目の動作を定義する Visual Studio 拡張機能を実装します。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  
  
3.  **\[新しいプロジェクト\]** ダイアログ ボックスの上部にある .NET Framework のバージョンの一覧で、**\[.NET Framework 4.5\]** が選択されていることを確認します。  
  
4.  **\[Visual Basic\]** ノードまたは **\[Visual C\#\]** ノードを展開し、**\[機能拡張\]** ノードをクリックします。  
  
    > [!NOTE]  
    >  **\[機能拡張\]** ノードは、Visual Studio SDK がインストールされている場合にのみ使用できます。  詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
5.  プロジェクト テンプレートの一覧で **\[VSIX プロジェクト\]** をクリックします。  
  
6.  **\[名前\]** ボックスに「**SiteColumnProjectItem**」と入力し、**\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の**ソリューション エクスプローラー**に **SiteColumnProjectItem** プロジェクトが追加されます。  
  
#### プロジェクト テンプレート プロジェクトを作成するには  
  
1.  **ソリューション エクスプローラー**でソリューション ノードのショートカット メニューを開き、**\[追加\]**、**\[新しいプロジェクト\]** の順にクリックします。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで**ソリューション エクスプローラー**にソリューション ノードが表示されるのは、[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)の **\[常にソリューションを表示\]** チェック ボックスがオンになっている場合だけです。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの上部にある .NET Framework のバージョンの一覧で、**\[.NET Framework 4.5\]** が選択されていることを確認します。  
  
3.  **\[Visual C\#\]** ノードまたは **\[Visual Basic\]** ノードを展開し、**\[機能拡張\]** ノードをクリックします。  
  
4.  プロジェクト テンプレートの一覧で **\[C\# プロジェクト テンプレート\]** または **\[Visual Basic プロジェクト テンプレート\]** テンプレートを選択します。  
  
5.  **\[名前\]** ボックスに「**SiteColumnProjectTemplate**」と入力し、**\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって **SiteColumnProjectTemplate** プロジェクトがソリューションに追加されます。  
  
6.  Class1 コード ファイルをプロジェクトから削除します。  
  
7.  Visual Basic プロジェクトを作成した場合は、次のファイルもプロジェクトから削除します。  
  
    -   MyApplication.Designer.vb  
  
    -   MyApplication.myapp  
  
    -   Resources.Designer.vb  
  
    -   Resources.resx  
  
    -   Settings.Designer.vb  
  
    -   Settings.settings  
  
#### 拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプローラー**でソリューション ノードのショートカット メニューを開き、**\[追加\]**、**\[新しいプロジェクト\]** の順にクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの上部にある .NET Framework のバージョンの一覧で、**\[.NET Framework 4.5\]** が選択されていることを確認します。  
  
3.  **\[Visual C\#\]** ノードまたは **\[Visual Basic\]** ノードを展開し、**\[Windows\]** ノードをクリックして、**\[クラス ライブラリ\]** テンプレートを選択します。  
  
4.  **\[名前\]** ボックスに「**ProjectItemTypeDefinition**」と入力し、**\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって、**ProjectItemTypeDefinition** プロジェクトがソリューションに追加され、既定の Class1 コード ファイルが開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
## 拡張機能プロジェクトの構成  
 コード ファイルおよびアセンブリ参照を追加し、拡張機能プロジェクトを構成します。  
  
#### プロジェクトを構成するには  
  
1.  ProjectItemTypeDefinition プロジェクトで、**SiteColumnProjectItemTypeProvider** という名前のコード ファイルを追加します。  
  
2.  メニュー バーで、**\[プロジェクト\]**、**\[参照の追加\]** の順に選択します。  
  
3.  **\[参照マネージャー \- ProjectItemTypeDefinition\]** ダイアログ ボックスで **\[アセンブリ\]** ノードを展開し、**\[フレームワーク\]** ノードをクリックして、\[System.ComponentModel.Composition\] チェック ボックスをオンにします。  
  
4.  **\[拡張機能\]** ノードを選択し、Microsoft.VisualStudio.SharePoint アセンブリの横にあるチェック ボックスをオンにして、**\[OK\]** をクリックします。  
  
## 新しい SharePoint プロジェクト項目の種類の定義  
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> インターフェイスを実装するクラスを作成して、新しいプロジェクト項目の種類の動作を定義します。  このインターフェイスは、新しい種類のプロジェクト項目を定義するたびに必ず実装します。  
  
#### 新しい SharePoint プロジェクト項目の種類を定義するには  
  
1.  **SiteColumnProjectItemTypeProvider** コード ファイルで、既定のコードを次のコードに置き換え、ファイルを保存します。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## Visual Studio プロジェクト テンプレートの作成  
 プロジェクト テンプレートを作成することにより、サイト内の列プロジェクト項目が含まれる SharePoint プロジェクトを他の開発者が作成できるようになります。  SharePoint プロジェクト テンプレートには、.csproj、.vbproj、.vstemplate など Visual Studio のすべてのプロジェクトで必要なファイルと、SharePoint プロジェクトに固有のファイルが含まれます。  詳細については、「[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)」を参照してください。  
  
 この手順では、SharePoint プロジェクトに固有のファイルを生成する空の SharePoint プロジェクトを作成します。  次に、これらのファイルが SiteColumnProjectTemplate プロジェクトから生成されるテンプレートに含まれるように、このプロジェクトに追加します。  また、SiteColumnProjectTemplate プロジェクト ファイルを構成して、**\[新しいプロジェクト\]** ダイアログ ボックス内でプロジェクト テンプレートが表示される場所も指定します。  
  
#### プロジェクト テンプレートのファイルを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の 2 つ目のインスタンスを管理者の資格情報で起動します。  
  
2.  **BaseSharePointProject** という名前の SharePoint 2010 プロジェクトを作成します。  
  
    > [!IMPORTANT]  
    >  **SharePoint カスタマイズ ウィザード**では、**\[ファーム ソリューションとして配置する\]** を選択しないでください。  
  
3.  空の要素項目をプロジェクトに追加し、その項目に「**Field1**」という名前を付けます。  
  
4.  プロジェクトを保存し、2 つ目の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] インスタンスを閉じます。  
  
5.  SiteColumnProjectItem ソリューションを開いている [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] インスタンスの**ソリューション エクスプローラー**で、**\[SiteColumnProjectTemplate\]** プロジェクト ノードのショートカット メニューを開き、**\[追加\]**、**\[既存の項目\]** の順にクリックします。  
  
6.  **\[既存項目の追加\]** ダイアログ ボックスで、ファイル拡張子の一覧を開き、**\[すべてのファイル \(\*.\*\)\]** をクリックします。  
  
7.  BaseSharePointProject プロジェクトが格納されているディレクトリで、key.snk ファイルを選択し、**\[追加\]** をクリックします。  
  
    > [!NOTE]  
    >  このチュートリアルで作成するプロジェクト テンプレートでは、テンプレートを使用して作成される各プロジェクトに署名するために、同じ key.snk ファイルが使用されます。  このサンプルを拡張してプロジェクト インスタンスごとに別の key.snk ファイルを作成する方法については、「[チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 2&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)」を参照してください。  
  
8.  手順 5. ～ 8. を繰り返して、BaseSharePointProject ディレクトリの指定されているサブフォルダーから次のファイルを追加します。  
  
    -   \\Field1\\Elements.xml  
  
    -   \\Field1\\SharePointProjectItem.spdata  
  
    -   \\Features\\Feature1\\Feature1.feature  
  
    -   \\Features\\Feature1\\Feature1.Template.xml  
  
    -   \\Package\\Package.package  
  
    -   \\Package\\Package.Template.xml  
  
     これらのファイルは SiteColumnProjectTemplate プロジェクトに直接追加します。プロジェクト内に Field1、Features、または Package の各サブフォルダーを再作成しないでください。  これらのファイルの詳細については、「[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)」を参照してください。  
  
#### \[新しいプロジェクト\] ダイアログ ボックスでのプロジェクト テンプレートの表示方法を構成するには  
  
1.  **ソリューション エクスプローラー**で、**\[SiteColumnProjectTemplate\]** プロジェクト ノードのショートカット メニューを開き、**\[プロジェクトのアンロード\]** をクリックします。  ファイルの変更を保存するかどうかを確認するメッセージが表示されたら、**\[はい\]** をクリックします。  
  
2.  **\[SiteColumnProjectTemplate\]** ノードのショートカット メニューを再度開き、**\[SiteColumnProjectTemplate.csproj の編集\]** または **\[SiteColumnProjectTemplate.vbproj の編集\]** をクリックします。  
  
3.  プロジェクト ファイル内で、次の `VSTemplate` 要素を見つけます。  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  この要素を次の XML に置き換えます。  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` 要素は、プロジェクトをビルドするとプロジェクト テンプレートが作成されるパス内の追加フォルダーを指定します。  ここで指定されたフォルダー内のプロジェクト テンプレートが使用可能になるのは、顧客が **\[新しいプロジェクト\]** ダイアログ ボックスを開き、**\[SharePoint\]** ノードを展開して、**\[2010\]** ノードを選択したときのみです。  
  
5.  ファイルを保存して閉じます。  
  
6.  **ソリューション エクスプローラー**で、**\[SiteColumnProjectTemplate\]** プロジェクトのショートカット メニューを開き、**\[プロジェクトの再読み込み\]** をクリックします。  
  
## プロジェクト テンプレート ファイルの編集  
 SiteColumnProjectTemplate プロジェクトで次のファイルを編集して、プロジェクト テンプレートの動作を定義します。  
  
-   AssemblyInfo.cs または AssemblyInfo.vb  
  
-   Elements.xml  
  
-   SharePointProjectItem.spdata  
  
-   Feature1.feature  
  
-   Package.package  
  
-   SiteColumnProjectTemplate.vstemplate  
  
-   ProjectTemplate.csproj または ProjectTemplate.vbproj  
  
 次の手順では、これらのファイルのいくつかに置き換え可能パラメーターを追加します。  置き換え可能パラメーターはトークンであり、先頭と末尾にはドル記号 \($\) が付いています。  ユーザーがこのプロジェクト テンプレートを使用してプロジェクトを作成するときに、Visual Studio によって自動的に新しいプロジェクト内のこれらのパラメーターが特定の値で置き換えられます。  詳細については、「[置き換え可能パラメーター](../sharepoint/replaceable-parameters.md)」を参照してください。  
  
#### AssemblyInfo.cs ファイルまたは AssemblyInfo.vb ファイルを編集するには  
  
1.  SiteColumnProjectTemplate プロジェクトで、AssemblyInfo.cs ファイルまたは AssemblyInfo.vb ファイルを開き、先頭に次のステートメントを追加します。  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     SharePoint プロジェクトの **\[サンドボックス ソリューション\]** プロパティが **\[True\]** に設定されている場合、Visual Studio によって <xref:System.Security.AllowPartiallyTrustedCallersAttribute> が AssemblyInfo コード ファイルに追加されます。  ただし、プロジェクト テンプレートの AssemblyInfo コード ファイルは、既定では <xref:System.Security> 名前空間をインポートしません。  この **using** ステートメントまたは **Imports** ステートメントを追加して、コンパイル エラーが発生しないようにする必要があります。  
  
2.  ファイルを保存して閉じます。  
  
#### Elements.xml ファイルを編集するには  
  
1.  SiteColumnProjectTemplate プロジェクトで、Elements.xml ファイルの内容を次の XML に置き換えます。  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     新しい XML により、サイト内の列の名前、その基本型、およびギャラリーでサイト内の列が表示されるグループを定義する `Field` 要素が追加されます。  このファイルの内容の詳細については、「[フィールド定義](http://go.microsoft.com/fwlink/?LinkId=184290)」を参照してください。  
  
2.  ファイルを保存して閉じます。  
  
#### SharePointProjectItem.spdata ファイルを編集するには  
  
1.  SiteColumnProjectTemplate プロジェクトで、SharePointProjectItem.spdata ファイルの内容を次の XML に置き換えます。  
  
    ```  
  
    <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                 xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
      </Files>   
    </ProjectItem>  
    ```  
  
     新しい XML により、ファイルは次のように変更されます。  
  
    -   `ProjectItem` 要素の `Type` 属性は、プロジェクト項目定義 \(先ほど作成した `SiteColumnProjectItemTypeProvider` クラス\) の <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> に渡すものと同じ文字列に変更されます。  
  
    -   `SupportedTrustLevels` 属性と `SupportedDeploymentScopes` 属性が `ProjectItem` 要素から削除されます。  信頼レベルと配置のスコープは ProjectItemTypeDefinition プロジェクトの `SiteColumnProjectItemTypeProvider` クラスに指定されているため、これらの属性値は不要です。  
  
     .spdata ファイルの内容の詳細については、「[SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)」を参照してください。  
  
2.  ファイルを保存して閉じます。  
  
#### Feature1.feature ファイルを編集するには  
  
1.  SiteColumnProjectTemplate プロジェクトで、Feature1.feature ファイルの内容を次の XML に置き換えます。  
  
    ```  
  
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
  
    -   `feature` 要素の `Id` 属性と `featureId` 属性の値が `$guid4$` に変更されます。  
  
    -   `projectItemReference` 要素の `itemId` 属性の値が `$guid2$` に変更されます。  
  
     .feature ファイルの詳細については、「[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)」を参照してください。  
  
2.  ファイルを保存して閉じます。  
  
#### Package.package ファイルを編集するには  
  
1.  SiteColumnProjectTemplate プロジェクトで、Package.package ファイルの内容を次の XML に置き換えます。  
  
    ```  
  
    <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
             Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
      <features>  
        <featureReference itemId="$guid4$" />  
      </features>  
    </package>  
    ```  
  
     新しい XML により、ファイルは次のように変更されます。  
  
    -   `package` 要素の `Id` 属性と `solutionId` 属性の値が `$guid3$` に変更されます。  
  
    -   `featureReference` 要素の `itemId` 属性の値が `$guid4$` に変更されます。  
  
     .package ファイルの詳細については、「[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)」を参照してください。  
  
2.  ファイルを保存して閉じます。  
  
#### SiteColumnProjectTemplate.vstemplate ファイルを編集するには  
  
1.  SiteColumnProjectTemplate プロジェクトで、SiteColumnProjectTemplate.vstemplate ファイルの内容を、次に示す XML セクションのいずれかと置き換えます。  
  
    -   Visual C\# プロジェクト テンプレートを作成している場合は、次の XML を使用します。  
  
    ```  
  
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
  
    ```  
  
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
  
    -   `Name` 要素が **Site Column** という値に設定されます \(この名前は **\[新しいプロジェクト\]** ダイアログ ボックスに表示されます\)。  
  
    -   各プロジェクト インスタンスに含まれているファイルごとに、`ProjectItem` 要素が追加されます。  
  
    -   名前空間 "http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005" が使用されます。  このソリューション内の他のプロジェクト ファイルでは、"http:\/\/schemas.microsoft.com\/developer\/msbuild\/2003" 名前空間が使用されます。  このため、XML スキーマ警告メッセージが生成されますが、このチュートリアルでは、これらを無視できます。  
  
     .vstemplate ファイルの内容の詳細については、「[Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)」を参照してください。  
  
2.  ファイルを保存して閉じます。  
  
#### ProjectTemplate.csproj ファイルまたは ProjectTemplate.vbproj ファイルを編集するには  
  
1.  SiteColumnProjectTemplate プロジェクトで、ProjectTemplate.csproj ファイルまたは ProjectTemplate.vbproj ファイルの内容を、次に示す XML セクションのいずれかと置き換えます。  
  
    -   Visual C\# プロジェクト テンプレートを作成している場合は、次の XML を使用します。  
  
    ```  
  
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
  
    ```  
  
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
  
    -   `TargetFrameworkVersion` 要素を使用して、.NET Framework 3.5 \(4.5 ではない\) が指定されます。  
  
    -   プロジェクトの出力に署名するための `SignAssembly` 要素と `AssemblyOriginatorKeyFile` 要素が追加されます。  
  
    -   SharePoint プロジェクトによって使用されるアセンブリ参照用の `Reference` 要素が追加されます。  
  
    -   Elements.xml や SharePointProjectItem.spdata など、プロジェクトの既定のファイルごとに要素が追加されます。  
  
2.  ファイルを保存して閉じます。  
  
## プロジェクト テンプレートを配置するための VSIX パッケージの作成  
 拡張機能を配置するには、**SiteColumnProjectItem** ソリューションの VSIX プロジェクトを使用して、VSIX パッケージを作成します。  まず、VSIX プロジェクトに含まれている source.extension.vsixmanifest ファイルを変更して、VSIX パッケージを構成します。  次に、ソリューションをビルドして VSIX パッケージを作成します。  
  
#### VSIX パッケージを構成および作成するには  
  
1.  **ソリューション エクスプローラー**で、**SiteColumnProjectItem** プロジェクトの source.extension.vsixmanifest ファイルをマニフェスト エディターで開きます。  
  
     source.extension.vsixmanifest ファイルが、すべての VSIX パッケージで必要になる extension.vsixmanifest ファイルの基礎となります。  このファイルの詳細については、「[VSIX 拡張機能のスキーマに関するリファレンス](http://msdn.microsoft.com/ja-jp/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)」を参照してください。  
  
2.  **\[製品名\]** ボックスに、「**Site Column**」と入力します。  
  
3.  **\[作成者\]** ボックスに「**Contoso**」と入力します。  
  
4.  **\[説明\]** ボックスに、「**A SharePoint project for creating site columns**」と入力します。  
  
5.  **\[アセット\]** タブをクリックし、**\[新規作成\]** をクリックします。  
  
     **\[Add New Asset\]** \(新しいアセットの追加\) ダイアログ ボックスが表示されます。  
  
6.  **\[種類\]** ボックスの一覧の **\[Microsoft.VisualStudio.ProjectTemplate\]** をクリックします。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `ProjectTemplate` 要素に対応します。  この要素は、プロジェクト テンプレートを格納する VSIX パッケージ内のサブフォルダーを示します。  詳細については、「[NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/ja-jp/87add64c-9dcd-495f-8815-209dab182cb1)」を参照してください。  
  
7.  **\[ソース\]** ボックスの一覧で **\[A project in current solution\]** \(現在のソリューション内のプロジェクト\) を選択します。  
  
8.  **\[プロジェクト\]** ボックスの一覧の **\[SiteColumnProjectTemplate\]** をクリックし、**\[OK\]** をクリックします。  
  
9. **\[新規作成\]** を再度クリックします。  
  
     **\[Add New Asset\]** \(新しいアセットの追加\) ダイアログ ボックスが表示されます。  
  
10. **\[種類\]** ボックスの一覧で **\[Microsoft.VisualStudio.MefComponent\]** を選択します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。  この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。  詳細については、「[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/ja-jp/8a813141-8b73-44c9-b80b-ca85bbac9551)」を参照してください。  
  
11. **\[ソース\]** ボックスの一覧で **\[A project in current solution\]** \(現在のソリューション内のプロジェクト\) を選択します。  
  
12. **\[プロジェクト\]** ボックスの一覧の **\[ProjectItemTypeDefinition\]** をクリックし、**\[OK\]** をクリックします。  
  
13. メニュー バーで **\[ビルド\]**、**\[ソリューションのビルド\]** の順にクリックし、プロジェクトがエラーなしでコンパイルされたことを確認します。  
  
## プロジェクト テンプレートのテスト  
 これで、プロジェクト テンプレートをテストする準備ができました。  まず、Visual Studio の実験用インスタンスで SiteColumnProjectItem ソリューションのデバッグを開始します。  次に、Visual Studio の実験用インスタンスで、**Site Column** プロジェクトをテストします。  最後に、SharePoint プロジェクトをビルドして実行し、サイト内の列が正常に機能することを確認します。  
  
#### ソリューションのデバッグを開始するには  
  
1.  管理者の資格情報で Visual Studio を再起動し、SiteColumnProjectItem ソリューションを開きます。  
  
2.  SiteColumnProjectItemTypeProvider コード ファイルで、`InitializeType` メソッド内のコードの 1 行目にブレークポイントを追加し、**F5** キーを押してデバッグを開始します。  
  
     Visual Studio によって、拡張機能が %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Site Column\\1.0 にインストールされ、Visual Studio の実験用インスタンスが開始されます。  このインスタンスの Visual Studio でプロジェクト項目をテストします。  
  
#### Visual Studio でプロジェクトをテストするには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで **\[ファイル\]**、**\[新規作成\]**、**\[プロジェクト\]** の順にクリックします。  
  
2.  \(プロジェクト テンプレートがサポートする言語に応じて\) **\[Visual C\#\]** ノードまたは **\[Visual Basic\]**  ノードを展開し、**\[SharePoint\]** ノードを展開して、**\[2010\]** ノードをクリックします。  
  
3.  プロジェクト テンプレートの一覧で、**\[Site Column\]** テンプレートをクリックします。  
  
4.  **\[名前\]** ボックスに「**SiteColumnTest**」と入力し、**\[OK\]** をクリックします。  
  
     **ソリューション エクスプローラー**に、**Field1** という名前のプロジェクト項目と共に新しいプロジェクトが表示されます。  
  
5.  Visual Studio のもう一方のインスタンスで、`InitializeType` メソッドの最初の方に設定したブレークポイントでコードが停止していることを確認し、**F5** キーを押して、プロジェクトのデバッグを続行します。  
  
6.  **ソリューション エクスプローラー**で、**\[Field1\]** ノードをクリックし、**F4** キーを押します。  
  
     **\[プロパティ\]** ウィンドウが開きます。  
  
7.  プロパティ一覧に **\[Example Property\]** というプロパティが表示されることを確認します。  
  
#### SharePoint でサイト内の列をテストするには  
  
1.  **ソリューション エクスプローラー**で、**\[SiteColumnTest\]** ノードをクリックします。  
  
2.  **\[プロパティ\]** ウィンドウで、**\[サイト URL\]** プロパティの横にあるテキスト ボックスをクリックし、「**http:\/\/localhost**」と入力します。  
  
     この手順により、デバッグに使用する開発用コンピューター上のローカル SharePoint サイトが指定されます。  
  
    > [!NOTE]  
    >  既定では **\[サイト URL\]** プロパティは空です。これは、Site Column プロジェクト テンプレートに、プロジェクトを作成するときにこの値を収集するウィザードが用意されていないためです。  開発者にこの値を尋ね、新しいプロジェクトでこのプロパティを構成するウィザードを追加する方法については、「[チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 2&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)」を参照してください。  
  
3.  **F5** キーを押します。  
  
     サイト列がパッケージ化され、プロジェクトの **\[サイト URL\]** プロパティで指定された SharePoint サイトに配置されます。  Web ブラウザーには、このサイトの既定のページが表示されます。  
  
    > [!NOTE]  
    >  **\[スクリプト デバッグが無効\]** ダイアログ ボックスが表示された場合は、**\[はい\]** をクリックしてプロジェクトをデバッグします。  
  
4.  **\[サイトの操作\]** メニューの **\[サイトの設定\]** をクリックします。  
  
5.  **\[サイトの設定\]** ページの **\[ギャラリー\]** ボックスの一覧で **\[サイト列\]** リンクをクリックします。  
  
6.  サイト内の列の一覧で、**\[SiteColumnTest\]** という名前の列を含む **\[Custom Columns\]** グループがあることを確認します。  
  
7.  Web ブラウザーを閉じます。  
  
## 開発コンピューターのクリーンアップ  
 プロジェクトのテストが終わったら、プロジェクト テンプレートを Visual Studio の実験用インスタンスから削除します。  
  
#### 開発コンピューターをクリーンアップするには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで **\[ツール\]**、**\[拡張機能と更新プログラム\]** の順にクリックします。  
  
     **\[拡張機能と更新プログラム\]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で **\[Site Column\]** 拡張機能を選択し、**\[アンインストール\]** をクリックします。  
  
3.  確認のダイアログ ボックスが表示されたら、**\[はい\]** をクリックして、拡張機能をアンインストールします。  
  
4.  **\[閉じる\]** をクリックするとアンインストールは完了です。  
  
5.  Visual Studio の両方のインスタンス \(実験用インスタンスと SiteColumnProjectItem ソリューションを開いたインスタンス\) を閉じます。  
  
## 次の手順  
 このチュートリアルを完了すると、プロジェクト テンプレートにウィザードを追加できるようになります。  ユーザーが Site Column プロジェクトを作成するときに、ウィザードが、デバッグに使用するサイトの URL と、新しいソリューションがサンドボックス ソリューションかどうかをユーザーに尋ね、この情報を使用して新しいプロジェクトを構成します。  また、ウィザードは、列に関する情報 \(基本型や、サイト内の列ギャラリーで列が表示されるグループなど\) を収集し、この情報を新しいプロジェクトの Elements.xml ファイルに追加します。  詳細については、「[チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 2&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)」を参照してください。  
  
## 参照  
 [チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 2&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  