---
title: "カスタム プロジェクトと Visual Studio 2017 項目テンプレートのアップグレード |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76437dff5aa59e4864216318e64a07245c15c68d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>カスタム プロジェクトと Visual Studio 2017 項目テンプレートをアップグレードします。
Visual Studio は、Visual Studio 2017 以降、.vsix または .msi がインストールされているプロジェクトと項目テンプレートを検出する方法を変更します。 カスタム プロジェクトや項目テンプレートを使用する拡張機能を所有している場合は、拡張機能を更新する必要があります。 このトピックでは、必要なことについて説明します。  
  
 この変更では、Visual Studio 2017 のみに影響します。 Visual Studio の以前のバージョンには影響しません。  
  
 VSIX 拡張機能の一部として、プロジェクトまたは項目テンプレートを作成する場合は、「[を作成するカスタム プロジェクトと項目テンプレート](../extensibility/creating-custom-project-and-item-templates.md)です。  
  
## <a name="template-scanning"></a>テンプレートのスキャン  
 以前は、 **devenv/setup**または**devenv/installvstemplates**プロジェクトと項目テンプレートを検索するローカル ディスクをスキャンします。 Preview 4 以降、スキャンは実行のみユーザー レベルの場所 (**%USERPROFILE%\Documents\\< Visual Studio のバージョン\>\My エクスポート テンプレート\\**) に使用されます。テンプレートによって生成された、**ファイル]/[エクスポート テンプレート**コマンド。  
  
 (非ユーザー)、他の場所の場所と、テンプレートの他の特性を指定する manifest(.vstman) ファイルを含める必要があります。 テンプレートの使用、.vstemplate ファイルと共に .vstman ファイルが生成されます。 .Vsix を使用して、拡張機能をインストールする場合は、Visual Studio 2017 内の拡張機能を再コンパイルしてこれを実行できます。 .Msi を使用する場合は、変更を手動で行う必要があります。 これらの変更のために実行する必要がありますの一覧は、次を参照してください。**でインストールする拡張機能をアップグレードします。MSI**このトピックで後述します。  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>プロジェクトまたは項目テンプレートを VSIX 拡張機能を更新する方法  
 この手順は、Visual Studio 2017 に方法を説明します。
1.  Visual Studio 2017 でソリューションを開きます。 コードをアップグレードするように求められます。 **[OK]** をクリックします。  
  
2.  アップグレードが完了したら、インストール対象のバージョンを変更する必要があります。 VSIX プロジェクトの source.extension.vsixmanifest ファイルを開き、選択、**インストールの対象**タブです。場合、**バージョン範囲**フィールドは**[14.0]**、 をクリックして**編集**し、Visual Studio 2017 を含むように変更します。 たとえば設定することができます**[14.0,15.0]** 、拡張機能をインストール、Visual Studio 2015 または Visual Studio 2017 年 1、またはに**[15.0]** Visual Studio 2017 だけにインストールします。  
  
3.  コードを再コンパイルします。  
  
4.  Visual Studio を閉じます。  
  
5.  VSIX をインストールします。  
  
6.  次の手順を実行して、更新プログラムをテストできます。  
  
    1.  ファイル変更のスキャンは、次のレジストリ キーでアクティブ化されます。  
  
         **reg は、hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1/reg:32 を追加します。**  
  
    2.  キーを追加した後に実行**devenv/installvstemplates**です。  
  
    3.  Visual Studio を閉じて再度開きます。 必要な場所に、テンプレートを見つける必要があります。  
  
    > [!NOTE]
    >  レジストリ キーが存在する場合は、Visual Studio 機能拡張プロジェクト テンプレートを使用できません。 レジストリ キーを削除する必要があります (再実行して**devenv/installvstemplates**) に使用します。  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>プロジェクトと項目テンプレートを展開するための推奨事項  
  
-   Zip 形式のテンプレート ファイルを使用しないでください。 テンプレート ファイルは、リソースとコンテンツを取得するために圧縮を解除する必要がありますを zip 圧縮され、したがってされますにコストが使用します。 代わりに、テンプレートの初期化を高速化する、独自のディレクトリの下の個別のファイルとしてプロジェクトと項目テンプレートを展開する必要があります。 VSIX 拡張機能 SDK のビルド タスクによって自動的に zip 形式のすべてのテンプレートが VSIX ファイルを作成中に解凍します。  
  
-   テンプレートの検出中に不要なリソース アセンブリの読み込みを回避するためにテンプレートの名前、説明、アイコンまたはプレビューのパッケージ/リソース ID のエントリを使用しないでください。 代わりに、ローカライズされた名前またはプロパティを使用して、各ロケールにテンプレートのエントリを作成するのに、ローカライズされたマニフェストを使用できます。  
  
-   ファイルのアイテムとしてテンプレートをインクルードする場合は、マニフェストの生成得ることができない、期待される結果。 その場合は、VSIX プロジェクトに手動で生成されたマニフェストを追加する必要があります。  
  
## <a name="file-changes-in-project-and-item-templates"></a>プロジェクトと項目テンプレートでファイルの変更  
Visual Studio 2015 と Visual Studio 2017 のバージョンのテンプレート ファイルの相違点のポイントを表示する、新しいファイルを正しく作成できるようにします。  
  
 Visual Studio 2015 で作成された既定プロジェクトの .vstemplate ファイルを次に示します。  
  
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
  
 次に、VSIX プロジェクトの再構築から生成される .vstman ファイル (できますで検索する VSIX プロジェクトのマニフェストのディレクトリ) を示します。  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
 によって提供される情報、 [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)要素は変わりません。 **\<VSTemplateContainer >**要素は、関連付けられているテンプレートの .vstemplate ファイルを指します。  
  
 Visual Studio 2015 で作成された既定の項目の .vstemplate ファイルを次に示します。  
  
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
  
 次に、VSIX プロジェクトの再構築から生成される .vstman ファイル (できますで検索する VSIX プロジェクトのマニフェストのディレクトリ) を示します。  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
 によって提供される情報、  **\<TemplateData >**要素は変わりません。 **\<VSTemplateContainer >**要素が関連付けられているテンプレートの .vstemplate ファイルを指す  
  
 .Vstman ファイルのさまざまな要素の詳細については、次を参照してください。 [Visual Studio テンプレート マニフェスト スキーマ リファレンス](../extensibility/visual-studio-template-manifest-schema-reference.md)です。  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>拡張機能のアップグレードをインストールします。MSI  
 MSI ベースの拡張機能によっては、一般的なテンプレートの場所は次のようにテンプレートを展開します。  
  
-   **\<Visual Studio インストール ディレクトリ > \Common7\IDE\\< ProjectTemplates/項目テンプレート >**  
  
-   **\<Visual Studio インストール ディレクトリ > \Common7\IDE\Extensions\\< ExtensionName\>\\< プロジェクト/項目テンプレート >**  
  
 拡張機能は、MSI ベースの展開を実行する場合は、テンプレート マニフェストを手動で生成し、拡張機能のセットアップに含まれていることを確認する必要があります。 上に挙げた .vstman 例を比較する必要があります、 [Visual Studio テンプレート マニフェスト スキーマ リファレンス](../extensibility/visual-studio-template-manifest-schema-reference.md)です。 どのようになるかを含める必要があります。  
  
 プロジェクトと項目テンプレートでは、個別マニフェストを作成し、テンプレート指定したルート ディレクトリ上を指す必要があります。 拡張機能とロケールあたり 1 つのマニフェストを作成する必要があります。  
  
## <a name="troubleshooting-template-installation"></a>テンプレートのインストールのトラブルシューティング  
 問題は、プロジェクトまたは項目テンプレートの展開に実行する場合は、診断ログの記録を有効にできます。  
  
1.  次の内容の pkgdef ファイル Common7\IDE\CommonExtensions フォルダーにインストール (例: C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) を作成します。  
  
     ```
     [$RootKey$\VsTemplate]
     "EnableTemplateDiscoveryLog"=dword:00000001
     ```

2. Windows search 内を検索して、「用開発者コマンド プロンプト」のインストールを開き、実行`devenv /updateConfiguration`です。

3.  Visual Studio を起動し、両方のテンプレート ツリーを初期化するために、新しいプロジェクトと新しい項目の追加ダイアログ ボックスを起動します。 テンプレートは、ログに表示されるよう**%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid は Visual Studio のインスタンスのインストール ID に相当します)。 各テンプレート ツリー初期化は、このログにエントリを追加します。  
  
 ログ ファイルには、次の列が含まれています。  
  
-   **FullPathToTemplate**、次の値を持ちます。  
  
    -   マニフェスト ベースの展開の場合は 1  
  
    -   ディスク ベースの展開の場合は 0  
  
-   **TemplateFileName**  
  
-   その他のテンプレートのプロパティ

注: するログ記録を無効にするには、pkgdef ファイルを削除するかの値を変更`EnableTemplateDiscoveryLog`に`dword:00000000`実行と`devenv /updateConfiguration`もう一度です。