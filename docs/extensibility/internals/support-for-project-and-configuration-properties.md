---
title: プロジェクトと構成プロパティのサポート |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76128710c377a6b9ec16f05064736b241ed0edba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954424"
---
# <a name="support-for-project-and-configuration-properties"></a>プロジェクトおよび構成プロパティのサポート
**プロパティ**ウィンドウで、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) は、プロジェクトと構成のプロパティを表示できます。 独自のプロジェクトの種類のプロパティ ページを指定するには、ユーザーがアプリケーションのプロパティを設定できるようにします。  
  
 プロジェクト ノードを選択して**ソリューション エクスプ ローラー**  をクリックし、**プロパティ**上、**プロジェクト** メニューの プロジェクトと構成を含むダイアログ ボックスを開くことができますプロパティ。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]、プロジェクトの種類のタブ付きページとしてこのダイアログ ボックスが表示されます。 これらの言語から派生し、 [General, Environment, オプション ダイアログ ボックス](../../ide/reference/general-environment-options-dialog-box.md)します。 詳細については、次を参照してください。[ビルド内にありません。チュートリアル: プロジェクトと構成のプロパティ (c#) を公開する](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)します。  
  
 Managed Package Framework (MPFProj) プロジェクトを作成して、新しいプロジェクト システムを管理するためのヘルパー クラスを提供します。 コードとコンパイル」の手順に従って、ソースを検索できる[- Visual Studio 2013 のプロジェクトの MPF](https://github.com/tunnelvisionlabs/MPFProj10)します。  
  
## <a name="persistence-of-project-and-configuration-properties"></a>プロジェクトと構成プロパティの永続化  
 プロジェクトと構成のプロパティは、たとえば、プロジェクトの種類に関連付けられているファイル名拡張子、.csproj、.vbproj、および .myproj を含むプロジェクト ファイルに保存されます。 通常、言語のプロジェクトは、プロジェクト ファイルを生成するのにテンプレート ファイルを使用します。 ただし、テンプレート プロジェクトの種類を関連付けるために実際にいくつかの方法はあります。 詳細については、次を参照してください。[テンプレート ディレクトリの説明 (します。Vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)します。  
  
 プロジェクトと構成のプロパティを作成するには、テンプレート ファイルに項目を追加します。 これらのプロパティはこのテンプレートを使用するプロジェクトの種類を使用して作成されたプロジェクトを利用できます。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] プロジェクトおよび MPFProj の両方を使用して、[ビルド内にありません。MSBuild の概要](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90))テンプレート ファイルのスキーマ。 これらのファイルでは、各構成の PropertyGroup セクションがあります。 プロジェクトのプロパティは、null 文字列に設定の構成引数を持つ最初の PropertyGroup セクションで通常は保持されます。  
  
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
  
 このプロジェクト ファイルで`<Name>`と`<SchemaVersion>`はプロジェクトのプロパティと`<Optimize>`構成プロパティします。  
  
 プロジェクト ファイルのプロジェクトと構成のプロパティを保持するプロジェクトの役目です。  
  
> [!NOTE]
>  プロジェクトでは、既定値とは異なるのみプロパティ値の永続化で永続化を最適化できます。  
  
## <a name="support-for-project-and-configuration-properties"></a>プロジェクトおよび構成プロパティのサポート  
 `Microsoft.VisualStudio.Package.SettingsPage`クラスは、プロジェクトと構成のプロパティ ページを実装します。 既定の実装`SettingsPage`汎用プロパティ グリッド内のユーザーにパブリック プロパティを提供しています。 `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids`メソッドから派生したクラスを選択する`SettingsPage`プロパティ グリッドのプロジェクト。 `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids`メソッドから派生したクラスを選択する`SettingsPage`のプロパティ グリッドを構成します。 プロジェクトの種類には、適切なプロパティ ページを選択するこれらのメソッドをオーバーライドする必要があります。  
  
 `SettingsPage`クラスおよび`Microsoft.VisualStudio.Package.ProjectNode`クラスはプロジェクトと構成のプロパティを保持するこれらのメソッドを提供します。  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty`プロジェクトのプロパティを保持します。  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty`構成プロパティを保持します。  
  
  > [!NOTE]
  >  実装、`Microsoft.VisualStudio.Package.SettingsPage`と`Microsoft.VisualStudio.Package.ProjectNode`クラスの使用、 `Microsoft.Build.BuildEngine` (MSBuild) メソッドを取得し、プロジェクト ファイルからプロジェクトと構成のプロパティを設定します。  
  
  派生したクラス`SettingsPage`実装する必要があります`Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges`と`Microsoft.VisualStudio.Package.SettingsPage.BindProperties`プロジェクト ファイルのプロジェクトまたは構成のプロパティを保持します。  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute とレジストリ パス  
 派生したクラス`SettingsPage`Vspackage の間で共有するように設計されています。 派生したクラスを作成するために VSPackage が可能に`SettingsPage`、追加、`Microsoft.VisualStudio.Shell.ProvideObjectAttribute`から派生したクラスに`Microsoft.VisualStudio.Shell.Package`します。  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 属性がアタッチされている VSPackage は重要ではありません。 VSPackage の登録時に[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、作成できる任意のオブジェクトのクラス id (CLSID) が登録されているようにへの呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A>に作成できます。  
  
 作成できるオブジェクトのレジストリ パスが組み合わせで決まります<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>単語、CLSID、およびオブジェクトの種類の guid。 場合`MyProjectPropertyPage`クラスは、{3c693da2-5bca-49b3-bd95-ffe0a39dd723} の guid を持つし、UserRegistryRoot HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp が、レジストリ パスに hkey_current_user \software\microsoft\visualstudio なります\8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}。  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>プロジェクトと構成プロパティの属性およびレイアウト  
 <xref:System.ComponentModel.CategoryAttribute>、 <xref:System.ComponentModel.DisplayNameAttribute>、および<xref:System.ComponentModel.DescriptionAttribute>属性は、レイアウト、ラベル付け、および汎用プロパティ ページで、プロジェクトと構成のプロパティの説明を決定します。 これらの属性は、カテゴリを確認、名、およびオプションの説明をそれぞれ表示します。  
  
> [!NOTE]
>  同等の属性、SRCategory、LocDisplayName、および SRDescription、ローカライズ文字列リソースを使用して、で定義されて[- Visual Studio 2013 のプロジェクトの MPF](https://github.com/tunnelvisionlabs/MPFProj10)します。  
  
 次のコードがあるとします。  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 `MyConfigProp`構成プロパティとして構成プロパティ ページに表示されます**マイ Config プロパティ** カテゴリで**My Category**します。 オプションが選択されている場合、説明、**マイ説明**、説明パネルに表示されます。  
  
## <a name="see-also"></a>関連項目  
 [追加して、プロパティ ページを削除します。](../../extensibility/adding-and-removing-property-pages.md)   
 [プロジェクト](../../extensibility/internals/projects.md)   
 [テンプレート ディレクトリの説明 (.Vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
