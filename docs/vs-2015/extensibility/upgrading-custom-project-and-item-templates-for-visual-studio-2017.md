---
title: カスタム プロジェクトと項目テンプレートを Visual Studio「15」のアップグレード |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9137510f8d6949271a255b14b293f59366048f77
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923447"
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-15"></a>Visual Studio「15」のカスタム プロジェクトと項目テンプレートをアップグレードします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

以降では、Visual Studio「15」Preview 4、Visual Studio では、.vsix、.msi インストールされているプロジェクトと項目テンプレートを検出する方法が変更されます。 カスタムのプロジェクトまたは項目テンプレートを使用する拡張機能を所有している場合は、拡張機能を更新する必要があります。 このトピックでは、必要な作業について説明します。  
  
 この変更では、Visual Studio「15」のみに影響します。 Visual Studio の以前のバージョンには影響しません。  
  
 VSIX 拡張機能の一部としてプロジェクトや項目テンプレートを作成する場合は、「[を作成するカスタム プロジェクトと項目テンプレート](../extensibility/creating-custom-project-and-item-templates.md)します。  
  
## <a name="template-scanning"></a>テンプレートのスキャン  
 以前は、 **devenv/setup**または**devenv/installvstemplates**プロジェクトと項目テンプレートを検索するローカル ディスクをスキャンします。 Preview 4 以降、スキャンが実行ユーザー レベルの場所に対してのみ (**%USERPROFILE%\Documents\\< Visual Studio バージョン\>\My Exported Templates\\**) に使用します。テンプレートによって生成された、**ファイル]/[エクスポート テンプレート**コマンド。  
  
 その他 (非ユーザー) の場所、場所と、テンプレートの他の特性を指定する manifest(.vstman) ファイルを含める必要があります。 テンプレートを使用している .vstemplate ファイルと共に .vstman ファイルが生成されます。 .Vsix を使用して、拡張機能をインストールする場合は、Visual Studio「15」Preview 2 で、拡張機能を再コンパイルしてこれを実行できます。 .Msi を使用する場合、変更を手動で行う必要があります。 これらの変更を行う必要があるものの一覧は、次を参照してください。**と共に拡張機能のインストールのアップグレードをします。MSI**このトピックで後述します。  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>プロジェクトまたは項目テンプレートで VSIX 拡張機能を更新する方法  
 この手順は、既存の VSIX 拡張機能が Visual Studio「15」Preview 2 の更新方法について説明します。  
  
1.  Visual Studio「15」Preview 2 では、ソリューションを開きます。 コードのアップグレードになります。 **[OK]** をクリックします。  
  
2.  アップグレードの完了したら、インストール先のバージョンを変更する必要があります。 VSIX プロジェクトの source.extension.vsixmanifest ファイルを開き、選択、**インストールの対象**タブ。場合、**バージョン範囲**フィールドは **[14.0]**、 をクリックして**編集**し、Visual Studio「15」を追加するために変更します。 設定するなど、 **[14.0,15.0]** または Visual Studio 2015 または Visual Studio「15」のいずれかに、拡張機能をインストールする **[15.0]** Visual Studio「15」のみにインストールします。  
  
3.  コードを再コンパイルします。  
  
4.  Visual Studio を閉じます。  
  
5.  VSIX をインストールします。  
  
6.  次の手順に従って、更新プログラムをテストできます。  
  
    1.  次のレジストリ キーがファイル変更のスキャンをアクティブにします。  
  
         **reg は、hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1/reg:32 を追加します。**  
  
    2.  キーを追加した後、実行**devenv/installvstemplates**します。  
  
    3.  Visual Studio を再度開きます。 予期された場所にテンプレートを探す必要があります。  
  
    > [!NOTE]
    >  レジストリ キーが存在する場合は、Visual Studio 機能拡張プロジェクト テンプレートは使用できません。 レジストリ キーを削除する必要があります (再実行して**devenv/installvstemplates**) それらを使用します。  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>プロジェクトと項目テンプレートをデプロイするための推奨事項  
  
-   Zip 形式のテンプレート ファイルを使用しないでください。 ファイルは、リソースやコンテンツを取得するために圧縮する必要があるテンプレートを zip 圧縮され、そのためされますなるほどを使用します。 代わりに、高速化するテンプレートの初期化に独自のディレクトリの下の個別のファイルとしてプロジェクトと項目テンプレートをデプロイする必要があります。 VSIX 拡張機能 SDK のビルド タスクは、zip 形式のテンプレートを VSIX ファイルを作成するときに自動的に解凍されます。  
  
-   テンプレートの検出中に不要なリソース アセンブリの読み込みを回避するためにテンプレート名、説明、アイコンまたはプレビューのパッケージ/リソース ID のエントリを使用しないでください。 代わりに、ローカライズされたマニフェストを使用して、ロケールごとに、ローカライズされた名前またはプロパティを使用するテンプレート エントリを作成することができます。  
  
-   ファイルのアイテムとしてテンプレートをインクルードする場合は、マニフェスト生成得ることができない、期待される結果。 その場合は、VSIX プロジェクトに手動で生成されたマニフェストを追加する必要があります。  
  
## <a name="file-changes-in-project-and-item-templates"></a>プロジェクトと項目テンプレート ファイルの変更  
 新しいファイルを正しく作成できるようにするは、Visual Studio 2015 バージョンと、テンプレート ファイルのバージョンの Visual Studio「15」の相違点のポイントを示します。  
  
 Visual Studio 2015 によって作成された既定プロジェクトの .vstemplate ファイルを次に示します。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ProjectTemplate1</Name>  
    <Description>ProjectTemplate1</Description>  
    <Icon>ProjectTemplate1.ico</Icon>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <SortOrder>1000</SortOrder>  
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
    <CreateNewFolder>true</CreateNewFolder>  
    <DefaultName>ProjectTemplate1</DefaultName>  
    <ProvideDefaultName>true</ProvideDefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">  
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>  
    </Project>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 次に、VSIX プロジェクトの再構築の原因となった .vstman ファイル (方で、VSIX プロジェクトのマニフェストのディレクトリ) を示します。  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ProjectTemplate1</Name>  
        <Description>ProjectTemplate1</Description>  
        <Icon>ProjectTemplate1.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>ProjectTemplate1</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 によって提供される情報、 [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)要素は変わりません。 **\<VSTemplateContainer >** 要素は、関連付けられたテンプレートの .vstemplate ファイルを指します。  
  
 Visual Studio 2015 によって作成された既定の項目 .vstemplate ファイルを次に示します。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ItemTemplate1</Name>  
    <Description>ItemTemplate1</Description>  
    <Icon>ItemTemplate1.ico</Icon>  
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    <DefaultName>Class.cs</DefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <References>  
      <Reference>  
        <Assembly>System</Assembly>  
      </Reference>  
    </References>  
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 次に、VSIX プロジェクトの再構築の原因となった .vstman ファイル (方で、VSIX プロジェクトのマニフェストのディレクトリ) を示します。  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 によって提供される情報、  **\<TemplateData >** 要素は変わりません。 **\<VSTemplateContainer >** 要素は、関連付けられたテンプレートの .vstemplate ファイルを指します  
  
 .Vstman ファイルのさまざまな要素の詳細については、次を参照してください。 [Visual Studio テンプレート マニフェスト スキーマ参照](../extensibility/visual-studio-template-manifest-schema-reference.md)します。  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>拡張機能のアップグレードがと共にインストールします。MSI  
 一部 MSI ベースの拡張機能は、次などの一般的なテンプレート場所にテンプレートを展開します。  
  
- **\<Visual Studio のインストール ディレクトリ > \Common7\IDE\\< ProjectTemplates/項目テンプレート >**  
  
- **\<Visual Studio のインストール ディレクトリ > \Common7\IDE\Extensions\\< ExtensionName\>\\< プロジェクト/項目テンプレート >**  
  
  拡張機能は、MSI ベースの展開を実行する場合は、テンプレート マニフェストを手動で生成し、拡張機能のセットアップに含まれていることを確認する必要があります。 上に挙げた .vstman 例を比較する必要があります、 [Visual Studio テンプレート マニフェスト スキーマ参照](../extensibility/visual-studio-template-manifest-schema-reference.md)します。 含める必要がありますを表示するには  
  
  プロジェクトと項目テンプレートでは、個別のマニフェストを作成する必要があり、ルート テンプレートのディレクトリとして指定された上記を指す必要があります。 拡張機能とロケールごとの 1 つのマニフェストを作成する必要があります。  
  
## <a name="troubleshooting-template-installation"></a>テンプレートのインストールのトラブルシューティング  
 プロジェクトまたは項目テンプレートのデプロイ時に問題が発生した場合は、診断ログを有効にできます。  
  
1. ログ記録を有効にするレジストリ キーを設定するのには、次のコマンドを実行します。  
  
    **reg は、HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate/v EnableTemplateDiscoveryLog/t REG_DWORD/d 1 を追加します。**  
  
2. Visual Studio を起動し、両方のテンプレートのツリーを初期化するために、新しいプロジェクトと新しい項目のダイアログ ボックスを起動します。 テンプレートは、ログに表示されている **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**します。 各テンプレート ツリーの初期化では、このログにエントリを追加します。  
  
   ログ ファイルには、次の列が含まれています。  
  
-   **FullPathToTemplate**、次の値を持ちます。  
  
    -   マニフェスト ベースの展開 1  
  
    -   ディスク ベースの展開の場合は 0  
  
-   **TemplateFileName**  
  
-   その他のテンプレートのプロパティ

