---
title: "プロジェクトおよび構成プロパティのサポート | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK の使用をサポートするプロジェクトのプロパティ"
  - "Visual Studio SDK に suppporting の構成のプロパティ"
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# プロジェクトおよび構成プロパティのサポート
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**プロパティ** ウィンドウで、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) は、プロジェクトおよび構成のプロパティを表示できます。 プロジェクトの種類のプロパティ ページを指定するには、ユーザーがアプリケーションのプロパティを設定できるようにします。  
  
 プロジェクト ノードを選択して **ソリューション エクスプ ローラー** クリックし、 **プロパティ** 上、 **プロジェクト** \] メニューの \[プロジェクトおよび構成のプロパティを含むダイアログ ボックスを開くことができます。[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] と [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], 、およびプロジェクトの管理\] ダイアログ ボックスのタブ付きページとしてこれらの言語から派生した型、 [\[全般\] \(\[オプション\] ダイアログ ボックス \- \[環境\]\)](../Topic/General,%20Environment,%20Options%20Dialog%20Box.md)です。 詳細については、次を参照してください。 [ビルドに存在しません: チュートリアル: プロジェクトの公開および構成のプロパティ \(c\#\)](http://msdn.microsoft.com/ja-jp/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)します。  
  
 管理されているパッケージのプロジェクトのフレームワーク \(MPFProj\) を作成して、新しいプロジェクト システムを管理するためのヘルパー クラスを提供します。 コードとコンパイル」の手順にソースを検索できる [Visual Studio 2013 のプロジェクトの MPF](http://mpfproj12.codeplex.com/)します。  
  
## プロジェクトおよび構成プロパティの永続化  
 たとえば、プロジェクトの種類に関連付けられているファイル名拡張子、.csproj、.vbproj ファイル、および .myproj のあるプロジェクト ファイルでは、プロジェクトおよび構成のプロパティが永続化されます。 通常、言語のプロジェクトは、プロジェクト ファイルを生成するのにテンプレート ファイルを使用します。 ただし、実際には、プロジェクトの種類のテンプレートを関連付けるためにいくつかの方法があります。 詳細については、次を参照してください。 [NIB: Visual Studio のテンプレート](http://msdn.microsoft.com/ja-jp/141fccaa-d68f-4155-822b-27f35dd94041) と [テンプレートのディレクトリの説明 \(します。Vsdir\) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)です。  
  
 プロジェクトおよび構成のプロパティを作成するには、テンプレート ファイルに項目を追加します。 このテンプレートを使用するプロジェクトの種類を使用して作成されたプロジェクトに、これらのプロパティを適用することはできます。[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] プロジェクトおよび MPFProj の両方を使用して、 [ビルドに存在しません: MSBuild の概要](http://msdn.microsoft.com/ja-jp/b588fd73-a45b-4706-908f-cc131bccfbde) テンプレート ファイルのスキーマです。 これらのファイルは、構成ごとに PropertyGroup セクションを持っています。 プロジェクトのプロパティは、通常、null 文字列に設定の構成の引数を持つ最初の PropertyGroup セクションに保存されます。  
  
 次のコードでは、基本的な MSBuild プロジェクト ファイルの先頭を示します。  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 このプロジェクト ファイルで `<Name>` と `<SchemaVersion>` プロジェクトのプロパティと `<Optimize>` 構成プロパティします。  
  
 プロジェクト ファイルのプロジェクトおよび構成のプロパティを保持するプロジェクトの責任です。  
  
> [!NOTE]
>  プロジェクトでは、既定値とは異なるだけプロパティ値の永続化で永続化を最適化できます。  
  
## プロジェクトおよび構成プロパティのサポート  
 `Microsoft.VisualStudio.Package.SettingsPage` クラスは、プロジェクトおよび構成のプロパティ ページを実装します。 既定の実装 `SettingsPage` 汎用プロパティ グリッド内のユーザーにパブリック プロパティを提供しています。`Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` メソッドから派生したクラスを選択する `SettingsPage` プロパティ グリッドのプロジェクトです。`Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` メソッドから派生したクラスを選択する `SettingsPage` のプロパティ グリッドを構成します。 プロジェクトの種類には、適切なプロパティ ページを選択するこれらのメソッドをオーバーライドする必要があります。  
  
 `SettingsPage` クラスおよび `Microsoft.VisualStudio.Package.ProjectNode` クラスは、プロジェクトおよび構成のプロパティを保持するこれらのメソッドを提供します。  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` プロジェクトのプロパティを永続化します。  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` 構成プロパティを永続化します。  
  
    > [!NOTE]
    >  実装、 `Microsoft.VisualStudio.Package.SettingsPage` と `Microsoft.VisualStudio.Package.ProjectNode` クラスの使用、 `Microsoft.Build.BuildEngine` \(MSBuild\) メソッドを取得し、プロジェクト ファイルからプロジェクトおよび構成のプロパティを設定します。  
  
 派生するクラス `SettingsPage` を実装する必要があります `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` と `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` プロジェクト ファイルのプロジェクトまたは構成のプロパティを保持します。  
  
## ProvideObjectAttribute とレジストリ パス  
 派生したクラス `SettingsPage` を Vspackage で共有できるよう設計されています。 派生したクラスを作成する VSPackage を可能にする `SettingsPage`, 、追加、 `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` から派生したクラスに `Microsoft.VisualStudio.Shell.Package`します。  
  
 [!code-cs[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 属性がアタッチされている VSPackage が重要ではありません。 VSPackage に登録するときに [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], 、作成できる任意のオブジェクトのクラス id \(CLSID\) が登録されているようにへの呼び出し <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> 独自に作成できます。  
  
 結合することで、作成可能なオブジェクトのレジストリ パスを決定 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, 、単語、CLSID、およびオブジェクトの種類の guid。 場合 `MyProjectPropertyPage` クラスには {3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723} の guid があり、UserRegistryRoot HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp が、レジストリ パスになります HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\CLSID\\{3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723} します。  
  
## プロジェクト構成プロパティの属性とレイアウト  
 <xref:System.ComponentModel.CategoryAttribute>, 、<xref:System.ComponentModel.DisplayNameAttribute>, 、および <xref:System.ComponentModel.DescriptionAttribute> 属性は、レイアウト、ラベル付け、および汎用プロパティ ページで、プロジェクトおよび構成のプロパティの説明を決定します。 これらの属性は、カテゴリを確認、名前、および、オプションの説明をそれぞれ表示します。  
  
> [!NOTE]
>  同等の属性、SRCategory、LocDisplayName、SRDescription、ローカリゼーション用の文字列リソースを使用およびで定義された [Visual Studio 2013 のプロジェクトの MPF](http://mpfproj12.codeplex.com/)します。  
  
 次のコードがあるとします。  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-cs[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 `MyConfigProp` 構成のプロパティとして構成プロパティ\] ページに表示されます **\[構成プロパティ** \] カテゴリで **My Category**します。 オプションが選択されている場合、説明、 **マイ説明**, 、説明のパネルに表示されます。  
  
## 参照  
 [ビルドに存在しません: チュートリアル: プロジェクトおよび構成プロパティ \(c\#\) を公開します。](http://msdn.microsoft.com/ja-jp/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [追加して、プロパティ ページを削除します。](../../extensibility/adding-and-removing-property-pages.md)   
 [Visual Studio の状態](/visual-cpp/misc/vspackage-state)   
 [プロジェクト](../../extensibility/internals/projects.md)   
 [NIB: Visual Studio テンプレート](http://msdn.microsoft.com/ja-jp/141fccaa-d68f-4155-822b-27f35dd94041)   
 [テンプレートのディレクトリの説明 \(します。Vsdir\) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)