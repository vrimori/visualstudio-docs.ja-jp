---
title: "Visual Studio「15」カスタムのプロジェクトおよび項目テンプレートをアップグレードする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: af2000e6c3649b625c54ed9dc2706d64642016ad
ms.lasthandoff: 02/22/2017

---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>カスタムのプロジェクトおよび項目テンプレートを Visual Studio 2017 をアップグレードします。
Visual Studio 2017 以降、Visual Studio のプロジェクト テンプレートと項目テンプレート、.vsix、.msi インストールされているが、検出された方法が変更されます。 カスタムのプロジェクトまたは項目テンプレートを使用する拡張機能を所有している場合は、拡張を更新する必要があります。 このトピックでは、必要なことについて説明します。  
  
 この変更では、Visual Studio 2017 のみに影響します。 Visual Studio の以前のバージョンには影響しません。  
  
 VSIX 拡張機能の一部として、プロジェクトまたは項目テンプレートを作成する場合は、「[を作成するカスタムのプロジェクトおよび項目テンプレート](../extensibility/creating-custom-project-and-item-templates.md)します。  
  
## <a name="template-scanning"></a>テンプレートのスキャン  
 以前は、 **devenv/setup**または**devenv/installvstemplates**プロジェクトと項目テンプレートを検索するローカル ディスクをスキャンします。 プレビュー 4 以降、スキャンが実行するユーザー レベルの場所に対してのみ (**%USERPROFILE%\Documents\\<Visual studio=""></Visual>\>\My Exported Templates\\**) で生成されたテンプレートに使用される、**ファイル/export テンプレート**コマンドです。  
  
 (非ユーザー)、他の場所、場所と、テンプレートの他の特性を指定する manifest(.vstman) ファイルを含める必要があります。 テンプレートの .vstemplate ファイルと共に .vstman ファイルが生成されます。 .Vsix を使用して、拡張機能をインストールする場合は、Visual Studio 2017 内の拡張機能を再コンパイルしてこれを実現できます。 .Msi を使用する場合は、変更を手動で行う必要があります。 これらの変更を行うために必要なものの一覧は、次を参照してください。**をインストールする拡張機能をアップグレードします。MSI**このトピックで後述します。  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>プロジェクトまたは項目テンプレートには VSIX 拡張機能を更新する方法  
 ここで Visual Studio 2017 を実施する方法について説明します。
1.  Visual Studio 2017 でソリューションを開きます。 コードのアップグレードが求められます。 **[OK]** をクリックします。  
  
2.  アップグレードの完了後は、インストール対象のバージョンを変更する必要があります。 VSIX プロジェクトの source.extension.vsixmanifest ファイルを開くし、選択、**インストールの対象** タブをクリックします。 場合、**バージョン範囲**フィールドは**[14.0]**、 をクリックして**編集**し、Visual Studio 2017 を含めるように変更します。 たとえば設定することができます**[14.0,15.0]**または Visual Studio 2015 または Visual Studio 2017 年に、拡張機能をインストールする**[15.0]** Visual Studio 2017 だけにインストールします。  
  
3.  コードを再コンパイルします。  
  
4.  Visual Studio を閉じます。  
  
5.  VSIX をインストールします。  
  
6.  次の手順に従って、更新プログラムをテストできます。  
  
    1.  次のレジストリ キーがファイルの変更のスキャンをアクティブにします。  
  
         **reg は、hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1/reg:32 を追加します。**  
  
    2.  キーを追加した後、実行**devenv/installvstemplates**します。  
  
    3.  Visual Studio を再度開きます。 予期される場所に、テンプレートを検索する必要があります。  
  
    > [!NOTE]
    >  レジストリ キーが存在する場合は、Visual Studio 機能拡張プロジェクト テンプレートを使用できません。 レジストリ キーを削除する必要があります (再実行して**devenv/installvstemplates**) に使用します。  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>プロジェクトおよび項目テンプレートを展開するための推奨事項  
  
-   Zip 形式のテンプレート ファイルを使用しないでください。 テンプレートのリソースやコンテンツを取得するために圧縮を解除する必要があるファイルを zip 圧縮され、そのためされますにコストが使用します。 代わりに、テンプレートの初期化を高速化する、独自のディレクトリの下の個別のファイルとしてプロジェクトおよび項目テンプレートを展開する必要があります。 VSIX 拡張機能 SDK のビルド タスクによって自動的に (zip 形式) のすべてのテンプレートが VSIX ファイルを作成するときに解凍します。  
  
-   テンプレートの検出時に不要なリソース アセンブリの読み込みを回避するためにテンプレートの名前、説明、アイコンまたはプレビューのパッケージ/リソース ID の入力を使用しないでください。 代わりに、ローカライズされた名前またはプロパティを使用する各ロケールのテンプレートのエントリを作成するのにローカライズされたマニフェストを使用できます。  
  
-   ファイルのアイテムとしてテンプレートをインクルードする場合は、マニフェストの生成得ることができない期待どおりの結果。 その場合は、VSIX プロジェクトに手動で生成されるマニフェストを追加する必要があります。  
  
## <a name="file-changes-in-project-and-item-templates"></a>プロジェクトおよび項目テンプレートのファイルの変更  
 新しいファイルを正しく作成できるように、Visual Studio 2015 のバージョンと、テンプレート ファイルのバージョンの Visual Studio「15」の違いの点を示します。  
  
 Visual Studio 2015 で作成された既定のプロジェクト .vstemplate ファイルを次に示します。  
  
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
  
 (これで見つかります VSIX プロジェクトのマニフェストのディレクトリ)、VSIX プロジェクトの再構築の原因として考え .vstman ファイルを次に示します。  
  
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
  
 返された情報に基づいて、 [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)要素に左右されません。 ** \<VSTemplateContainer >**要素は関連付けられているテンプレートの .vstemplate ファイルを指します。  
  
 Visual Studio 2015 で作成された既定の項目 .vstemplate ファイルを次に示します。  
  
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
  
 (これで見つかります VSIX プロジェクトのマニフェストのディレクトリ)、VSIX プロジェクトの再構築の原因として考え .vstman ファイルを次に示します。  
  
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
  
 返された情報に基づいて、 ** \<TemplateData >**要素に左右されません。 ** \<VSTemplateContainer >**要素が関連付けられているテンプレートの .vstemplate ファイルを指す  
  
 .Vstman ファイルのさまざまな要素の詳細については、次を参照してください。 [Visual Studio テンプレート マニフェスト スキーマ リファレンス](../extensibility/visual-studio-template-manifest-schema-reference.md)します。  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>と共に拡張機能のアップグレードをインストールします。MSI  
 MSI ベースの拡張機能によっては、一般的なテンプレートの位置、次のようにテンプレートを展開します。  
  
-   **\<Visual Studio インストール ディレクトリ > \Common7\IDE\\<ProjectTemplates temtemplates="">**</ProjectTemplates>  
  
-   **\<Visual Studio インストール ディレクトリ > \Common7\IDE\Extensions\\<>\>\\<Project temtemplates="">**</Project>  
  
 拡張機能では、MSI ベースの展開を実行する場合は、テンプレートのマニフェストを手動で生成し、拡張機能のセットアップに含まれていることを確認する必要があります。 上に示した .vstman 例を比較する必要があり、 [Visual Studio テンプレート マニフェスト スキーマ リファレンス](../extensibility/visual-studio-template-manifest-schema-reference.md)します。 表示を含める必要があります。  
  
 プロジェクトおよび項目テンプレート用の個別のマニフェストを作成し、テンプレート指定したルート ディレクトリ上を指す必要があります。 拡張機能とロケールごとに&1; つのマニフェストを作成する必要があります。  
  
## <a name="troubleshooting-template-installation"></a>テンプレートのインストールのトラブルシューティング  
 プロジェクトまたは項目テンプレートの展開の問題が発生した場合は、診断ログを有効にすることができます。  
  
1.  ログ記録を有効にするレジストリ キーを設定するのには、次のコマンドを実行します。  
  
     **reg は、HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate/v EnableTemplateDiscoveryLog/t REG_DWORD/d 1 を追加します。**  
  
2.  Visual Studio を起動し、両方のテンプレート ツリーを初期化するために、新しいプロジェクトと新しい項目の追加ダイアログ ボックスを起動します。 テンプレートは、ログに表示されるよう**%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**します。 各テンプレート ツリーの初期化は、このログにエントリを追加します。  
  
 ログ ファイルには、次の列が含まれています。  
  
-   **FullPathToTemplate**、次の値を持ちます。  
  
    -   マニフェスト ベースの展開の場合は&1;  
  
    -   ディスク ベースの展開の場合は&0;  
  
-   **TemplateFileName**  
  
-   その他のテンプレートのプロパティ
