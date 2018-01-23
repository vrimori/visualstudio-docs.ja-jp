---
title: "プロジェクトと構成プロパティのサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e31f4feda55469d2740b32b0eac5d9cfba286d0c
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="support-for-project-and-configuration-properties"></a>プロジェクトと構成プロパティのサポート
**プロパティ** ウィンドウで、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) は、プロジェクトと構成のプロパティを表示できます。 ユーザーがアプリケーションのプロパティを設定できるように、プロジェクトの種類のプロパティ ページを使用できます。  
  
 プロジェクト ノードを選択して**ソリューション エクスプ ローラー**クリックし、**プロパティ**上、**プロジェクト**] メニューの [プロジェクトと構成を含むダイアログ ボックスを開くことができますプロパティ。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]、プロジェクトの種類のタブ付きページとしてこのダイアログ ボックスが表示されます。 これらの言語から派生し、[全般、環境、オプションダイアログ ボックス](../../ide/reference/general-environment-options-dialog-box.md)です。 詳細については、次を参照してください。[ビルド内にありません: チュートリアル: プロジェクトの公開および構成のプロパティ (c#)](http://msdn.microsoft.com/en-us/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)です。  
  
 (MPFProj) のプロジェクト用 Managed Package Framework は、作成して、新しいプロジェクト システムを管理するためのヘルパー クラスを提供します。 コードとコンパイル」の手順にソースを検索できる[プロジェクトの Visual Studio 2013 の MPF](http://mpfproj12.codeplex.com/)です。  
  
## <a name="persistence-of-project-and-configuration-properties"></a>プロジェクトと構成プロパティの永続化  
 プロジェクトと構成のプロパティは、たとえば、プロジェクトの種類に関連付けられているファイル名拡張子、.csproj、.vbproj ファイル、および .myproj を含むプロジェクト ファイルに保存されます。 通常、言語のプロジェクトは、プロジェクト ファイルを生成するのにテンプレート ファイルを使用します。 ただし、プロジェクトの種類のテンプレートを関連付けるために実際にはいくつかの方法があります。 詳細については、次を参照してください。[テンプレート ディレクトリの説明 (です。Vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)です。  
  
 プロジェクトと構成のプロパティを作成するには、項目テンプレート ファイルを追加します。 これらのプロパティはこのテンプレートを使用するプロジェクトの種類を使用して作成されたプロジェクトに使用できるになります。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]プロジェクトおよび MPFProj の両方を使用して、[ビルド内にありません: MSBuild の概要](http://msdn.microsoft.com/en-us/b588fd73-a45b-4706-908f-cc131bccfbde)テンプレート ファイルのスキーマです。 これらのファイルは、各構成の PropertyGroup セクションを持っています。 プロジェクトのプロパティは、通常は、null 文字列に設定の構成の引数が存在する最初の PropertyGroup セクションで永続化されます。  
  
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
  
 このプロジェクト ファイルで`<Name>`と`<SchemaVersion>`プロジェクト プロパティおよび`<Optimize>`構成プロパティします。  
  
 プロジェクト ファイルのプロジェクトと構成のプロパティを保持するプロジェクトの役割です。  
  
> [!NOTE]
>  プロジェクトは、既定値とは異なるのみプロパティ値の永続化で永続化を最適化できます。  
  
## <a name="support-for-project-and-configuration-properties"></a>プロジェクトと構成プロパティのサポート  
 `Microsoft.VisualStudio.Package.SettingsPage`クラスがプロジェクトと構成のプロパティ ページを実装します。 既定の実装`SettingsPage`汎用プロパティ グリッド内のユーザーにパブリック プロパティを提供します。 `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids`メソッドから派生したクラスを選択する`SettingsPage`プロパティ グリッドのプロジェクトです。 `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids`メソッドから派生したクラスを選択する`SettingsPage`プロパティ グリッドの構成。 プロジェクトの種類は、適切なプロパティ ページを選択するこれらのメソッドをオーバーライドする必要があります。  
  
 `SettingsPage`クラスおよび`Microsoft.VisualStudio.Package.ProjectNode`クラスがプロジェクトと構成のプロパティを保持するこれらのメソッドを提供します。  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`および`Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty`プロジェクトのプロパティを永続化します。  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`および`Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty`構成プロパティを保持します。  
  
    > [!NOTE]
    >  実装、`Microsoft.VisualStudio.Package.SettingsPage`と`Microsoft.VisualStudio.Package.ProjectNode`クラスを使用して、 `Microsoft.Build.BuildEngine` (MSBuild) メソッドを取得し、プロジェクト ファイルからプロジェクトと構成のプロパティを設定します。  
  
 派生するクラス`SettingsPage`実装する必要があります`Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges`と`Microsoft.VisualStudio.Package.SettingsPage.BindProperties`プロジェクト ファイルのプロジェクトまたは構成のプロパティを保持します。  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute とレジストリ パス  
 派生したクラス`SettingsPage`Vspackage の間で共有するよう設計されています。 派生したクラスを作成する VSPackage を可能にする`SettingsPage`、追加、`Microsoft.VisualStudio.Shell.ProvideObjectAttribute`から派生したクラスに`Microsoft.VisualStudio.Shell.Package`です。  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 属性のアタッチ先 VSPackage は重要ではありません。 VSPackage を登録するときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、作成できる任意のオブジェクトのクラス id (CLSID) が登録されているようにへの呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A>独自に作成できます。  
  
 結合することで、作成できるオブジェクトのレジストリ パスを決定<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>単語、CLSID、およびオブジェクトの種類の guid。 場合`MyProjectPropertyPage`クラスには、{3c693da2-5bca-49b3-bd95-ffe0a39dd723} の guid と、UserRegistryRoot HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp は、レジストリ パスに HKEY_CURRENT_USER\Software\Microsoft\VisualStudio なります\8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}。  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>プロジェクトと構成プロパティの属性およびレイアウト  
 <xref:System.ComponentModel.CategoryAttribute>、 <xref:System.ComponentModel.DisplayNameAttribute>、および<xref:System.ComponentModel.DescriptionAttribute>属性は、レイアウト、ラベル付け、および汎用プロパティ ページで、プロジェクトと構成のプロパティの説明を確認します。 これらの属性は、カテゴリを確認、名前、およびオプションの説明をそれぞれ表示します。  
  
> [!NOTE]
>  同等の属性、SRCategory、LocDisplayName、SRDescription、文字列リソースのローカライズ用と使用で定義された[プロジェクトの Visual Studio 2013 の MPF](http://mpfproj12.codeplex.com/)です。  
  
 次のコードがあるとします。  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 `MyConfigProp`として構成プロパティ ページで構成プロパティが表示されます**マイ Config プロパティ** カテゴリで、**マイ カテゴリ**です。 オプションを選択する場合、説明、**マイ説明**、[説明] パネルに表示されます。  
  
## <a name="see-also"></a>参照  
 [追加して、プロパティ ページを削除します。](../../extensibility/adding-and-removing-property-pages.md)   
 [プロジェクト](../../extensibility/internals/projects.md)   
 [テンプレート ディレクトリの説明 (.Vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
