---
title: Visual Studio の SharePoint ツールの拡張機能の配置 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58b430d1331a12e080d238d34a4817afea8585d1
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326866"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Visual Studio の SharePoint ツールの拡張機能をデプロイします。

SharePoint ツール拡張機能を展開するには、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]拡張機能のアセンブリおよび拡張機能を配布するその他のファイルを含む拡張機能 (VSIX) パッケージ。 VSIX パッケージは、Open Packaging Conventions (OPC) 標準に準拠した圧縮ファイルです。 VSIX パッケージが、 *.vsix*拡張機能。

VSIX パッケージを作成した後、その他のユーザーは、拡張機能をインストールする .vsix ファイルを実行できます。 ユーザーは、拡張機能をインストールしたときに、%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions フォルダーにすべてのファイル インストールされます。 VSIX パッケージをアップロードする、拡張機能を展開する、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイト、またはすることができます、パッケージ、お客様に配布のパッケージをネットワーク共有またはその他のいくつかの Web サイトをホストしているなど、他の方法でします。

VSIX パッケージの作成および展開することの詳細については、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847)を参照してください[Visual Studio 拡張機能の配布](../extensibility/shipping-visual-studio-extensions.md)します。

 使用して VSIX パッケージを作成することができます、 **VSIX プロジェクト**には、Visual Studio は、テンプレートでは、VSIX パッケージを手動で作成することができます。

## <a name="use-vsix-projects-to-create-vsix-packages"></a>VSIX プロジェクトを使用して、VSIX パッケージを作成するには

使用することができます、 **VSIX プロジェクト**SharePoint ツールの拡張機能の VSIX パッケージを作成する Visual Studio SDK によって提供されるテンプレート。 VSIX プロジェクトを使用して VSIX パッケージを手動で作成をいくつかの利点を提供します。

-   Visual Studio は、プロジェクトをビルドするときに、VSIX パッケージを自動的に生成されます。 展開ファイルをパッケージに追加して、パッケージの [Content_Types] .xml ファイルを作成するなどのタスクが実行されます。

-   VSIX パッケージに、拡張機能プロジェクトとプロジェクト テンプレートと項目テンプレートなどの他のファイルのビルド出力を含めるよう、VSIX プロジェクトを構成することができます。

詳細については、VSIX プロジェクトを使用して、次を参照してください。 [VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)します。

### <a name="organize-your-projects"></a>プロジェクトを整理します。

既定では、VSIX プロジェクトはアセンブリではない、VSIX パッケージを生成するだけです。 そのため、通常は実装しない SharePoint ツール拡張機能を VSIX プロジェクト。 一般に、少なくとも 2 つのプロジェクトで作業します。

-   VSIX プロジェクト。

-   拡張機能を実装するクラス ライブラリ プロジェクト。

操作することがありますもその他のプロジェクトで特定の種類の拡張機能。

-   拡張機能で使用される任意の SharePoint コマンドを実装するクラス ライブラリ プロジェクト。 このシナリオを実証するチュートリアルでは、次を参照してください。[チュートリアル: サーバー エクスプ ローラー web パーツを表示する拡張](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)します。

-   プロジェクト テンプレートまたは項目テンプレート プロジェクトを拡張機能は、SharePoint プロジェクト項目の新しい型を定義している場合、プロジェクト テンプレート、または項目テンプレートを作成します。 このシナリオを実証するチュートリアルでは、次を参照してください。[チュートリアル: 項目テンプレート、第 1 部でのカスタム動作プロジェクト項目の作成](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)です。

-   拡張機能には、テンプレートが含まれている場合、プロジェクト テンプレート、または項目テンプレートのカスタム ウィザードを実装するクラス ライブラリ プロジェクト。 このシナリオを実証するチュートリアルでは、次を参照してください。[チュートリアル: 項目テンプレート、第 2 部でのカスタム動作プロジェクト項目の作成](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)です。

同じ Visual Studio ソリューション内のすべてのプロジェクトを含めると場合、は、クラス ライブラリ プロジェクトのビルド出力を含める に、VSIX プロジェクトの source.extension.vsixmanifest ファイルを変更できます。

### <a name="edit-the-vsix-manifest"></a>VSIX マニフェストを編集します。

拡張機能に含めるすべてのアイテムのエントリを含めるに VSIX プロジェクトの source.extension.vsixmanifest ファイルを編集する必要があります。 Source.extension.vsixmanifest ファイルを開くには、そのショートカット メニューから、ファイル内の XML を編集するための UI を提供するデザイナーで、ファイルが表示されます。 詳細については、次を参照してください。 [VSIX マニフェスト デザイナー](../extensibility/vsix-manifest-designer.md)します。

エントリは、次の項目の source.extension.vsixmanifest ファイルを追加する必要があります。

-   拡張機能のアセンブリ。

-   拡張機能で使用される任意の SharePoint コマンドを実装するアセンブリ。

-   プロジェクト テンプレートや項目テンプレート、拡張機能に関連付けられています。

-   拡張機能に関連付けられているテンプレートのカスタム ウィザード。

次の手順では、これらの各項目の .vsixmanifest ファイルにエントリを追加する方法について説明します。

#### <a name="to-include-the-extension-assembly"></a>拡張機能アセンブリを含める

1.  VSIX プロジェクトの source.extension.vsixmanifest ファイルのショートカット メニューを開きし、**開く**します。

     ファイルは、デザイナーが開きます。

2.  **資産** タブ、エディターの選択、**新規**ボタンをクリックします。

     **新しい資産の追加** ダイアログ ボックスが表示されます。

3.  **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**します。

4.  **ソース**ボックスの一覧で、次の手順のいずれかを実行します。

    -   拡張機能のアセンブリは、VSIX プロジェクトと同じソリューション内にあるプロジェクトから構築された場合、選択**現在のソリューションでプロジェクトを**します。 **プロジェクト**一覧で、プロジェクトの名前を選択します。

    -   拡張機能のアセンブリがプロジェクト内のファイルとして含める場合は、選択**ファイル システム上の**します。 **パス**を一覧表示、拡張機能アセンブリ ファイルを完全なパスを入力するかを使用して、**参照** ボタンを見つけて、アセンブリ ファイルを選択します。

5.  **[OK]** を選択します。

#### <a name="to-include-a-sharepoint-command-assembly"></a>SharePoint コマンドのアセンブリを含める

1.  VSIX プロジェクトの source.extension.vsixmanifest ファイルのショートカット メニューを開きし、、**開く**ボタンをクリックします。

     ファイルがデザイナーで開きます。

2.  **資産**セクション、エディターの選択、**新規**ボタンをクリックします。

     **新しい資産の追加** ダイアログ ボックスが表示されます。

3.  **型**ボックスに、入力**SharePoint.Commands.v4**します。

4.  **ソース**ボックスの一覧で、次の手順のいずれかを実行します。

    -   コマンドのアセンブリは、VSIX プロジェクトと同じソリューション内にあるプロジェクトから構築された場合、選択**現在のソリューションでプロジェクトを**します。 **プロジェクト**一覧で、プロジェクトの名前を選択します。

    -   コマンドのアセンブリがファイルとしてプロジェクトに含まれる場合は、選択**ファイル システム上の**します。 **パス**を一覧表示、拡張機能アセンブリ ファイルを完全なパスを入力するかを使用して、**参照** ボタンを見つけて、アセンブリ ファイルを選択します。

5.  **[OK]** を選択します。

#### <a name="to-include-a-template-that-you-create"></a>作成したテンプレートを含める

1.  VSIX プロジェクトの source.extension.vsixmanifest ファイルのショートカット メニューを開きし、、**開く**ボタンをクリックします。

     ファイルがデザイナーで開きます。

2.  **資産**セクション、エディターの選択、**新規**ボタンをクリックします。

     **新しい資産の追加** ダイアログ ボックスが表示されます。

3.  **型**一覧で、選択**Microsoft.VisualStudio.ProjectTemplate**または **[microsoft.visualstudio.itemtemplate]** します。

4.  **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。

5.  **プロジェクト**ボックスの一覧で、プロジェクトの名前を選択し、、 **OK**ボタン。

6.  **ソリューション エクスプ ローラー**プロジェクト テンプレートや項目テンプレート プロジェクトのショートカット メニューを開き、選択し、**プロジェクトのアンロード**します。

7.  プロジェクト ノードのショートカット メニューを再度開き、選択**編集***YourTemplateProjectName***.csproj**または**編集***YourTemplateProjectName***します。vbproj**します。

8.  プロジェクト ファイルで次の `VSTemplate` 要素を見つけます。

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. この要素を次の XML に置き換えます。

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` 要素は、プロジェクトをビルドするとプロジェクト テンプレートが作成されるパス内の追加フォルダーを指定します。 ここで指定したフォルダーは、顧客を開く場合にのみ、項目テンプレートが利用できるということを確認、**新しいプロジェクトの追加** ダイアログ ボックスで、展開、 **SharePoint**ノードを選択し、 **2010**ノード。

10. ファイルを保存して閉じます。

11. **ソリューション エクスプ ローラー**プロジェクト テンプレートや項目テンプレート プロジェクトのショートカット メニューを開き、選択し、**プロジェクトの再読み込み**します。

#### <a name="to-include-a-template-that-you-create-manually"></a>手動で作成したテンプレートを含める

1.  VSIX プロジェクト テンプレートを格納するプロジェクトに新しいフォルダーを追加します。

2.  この新しいフォルダーの下、次のサブフォルダーを作成し、テンプレート (.zip) ファイルを追加、*ロケール ID*フォルダー。

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *ロケール ID*

     *YourTemplateName*.zip

     たとえば、英語 (米国) ロケールをサポートする ContosoCustomAction.zip という名前の項目テンプレートがあれば、完全なパス可能性があります*ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*します。

3.  **ソリューション エクスプ ローラー**、テンプレート ファイルを選択 (*YourTemplateName*.zip)。

4.  **プロパティ**ウィンドウで、設定、**ビルド アクション**プロパティを**コンテンツ**します。

5.  Source.extension.vsixmanifest ファイルのショートカット メニューを開き、選択し、**オープン**します。

     ファイルがデザイナーで開きます。

6.  **資産**セクション、エディターの選択、**新規**ボタンをクリックします。

     **新しい資産の追加** ダイアログ ボックスが表示されます。

7.  **型**一覧で、選択 **[microsoft.visualstudio.itemtemplate]** または**Microsoft.VisualStudio.ProjectTemplate**します。

8.  **ソース**一覧で、選択**ファイル システム上の**します。

9. **パス**フィールドに、アセンブリへの完全なパスを入力 (たとえば、 *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*を使用して、または、 **参照**を見つけて、アセンブリの選択ボタンをクリックし、、 **OK**ボタンをクリックします。

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>プロジェクトのテンプレートや項目テンプレートのウィザードを含める

1.  VSIX プロジェクトの source.extension.vsixmanifest ファイルのショートカット メニューを開きし、**開く**します。

     ファイルがデザイナーで開きます。

2.  **資産**セクション、エディターの選択、**新規**ボタンをクリックします。

     **新しい資産の追加** ダイアログ ボックスが表示されます。

3.  **型**一覧で、選択 **[microsoft.visualstudio.assembly]** します。

4.  **ソース**ボックスの一覧で、次の手順のいずれかを実行します。

    -   ウィザード アセンブリには、VSIX プロジェクトと同じソリューション内にあるプロジェクトから構築された、場合**現在のソリューションでプロジェクトを**します。 **プロジェクト**一覧で、プロジェクトの名前を選択します。

    -   ウィザード アセンブリがプロジェクト内のファイルとして含める場合は、選択**ファイル システム上の**します。 **パス**フィールド、アセンブリ ファイルを完全なパスを入力するかを使用して、**参照**を見つけて、アセンブリの選択ボタンをクリックします。

5.  **[OK]** を選択します。

### <a name="related-walkthroughs"></a>関連するチュートリアル

次の表は、VSIX プロジェクトを使用して、さまざまな種類の SharePoint ツール拡張機能をデプロイする方法について説明するチュートリアルを一覧表示します。

|拡張機能の種類|関連するチュートリアル|
|--------------------|--------------------------|
|拡張機能アセンブリのみを含む拡張機能|[チュートリアル: SharePoint プロジェクト項目の種類を拡張します。](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [チュートリアル: SharePoint プロジェクト拡張機能を作成します。](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [チュートリアル: は、サーバー エクスプ ローラー拡張機能では、SharePoint クライアント オブジェクト モデルを呼び出す](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|SharePoint コマンドを含む拡張機能|[チュートリアル: SharePoint プロジェクトのカスタム配置手順を作成します。](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [チュートリアル: web パーツを表示するサーバー エクスプ ローラーの拡張します。](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [チュートリアル: プロジェクト テンプレート、第 2 部でのサイト列プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Visual Studio テンプレートを含む拡張機能|[チュートリアル: 項目テンプレート、第 1 部でのカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [チュートリアル: プロジェクト テンプレート、第 1 部でのサイト列プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|テンプレート ウィザードを含む拡張機能|[チュートリアル: 項目テンプレート、第 2 部でのカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [チュートリアル: プロジェクト テンプレート、第 2 部でのサイト列プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>VSIX パッケージを手動で作成します。

SharePoint ツール拡張機能の VSIX パッケージを手動で作成する場合は、次の手順に従います。

1.  新しいフォルダーには、extension.vsixmanifest ファイルと [Content_Types] .xml ファイルを作成します。 詳細については、次を参照してください。 [VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)します。

2.  Windows エクスプ ローラーで 2 つの XML ファイルを含むフォルダーを右クリックし、送信 をクリックし、圧縮 (zip 形式) フォルダー をクリックします。 Filename.vsix、Filename には、パッケージをインストールする再頒布可能ファイルの名前には、結果として得られる .zip ファイルを変更します。

3.  VSIX パッケージに、拡張機能アセンブリを追加します。 拡張機能には、SharePoint コマンドが含まれている場合も、VSIX パッケージする SharePoint コマンドを実装するアセンブリを追加します。

4.  Extension.vsixmanifest ファイルを変更します。

    -   追加、`Microsoft.VisualStudio.MefComponent`の下の要素、`Assets`要素、および、VSIX パッケージで、拡張機能を実装するアセンブリの相対パスに新しい要素の値を設定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)します。

    -   拡張機能には、SharePoint のサーバー オブジェクト モデルを呼び出す SharePoint コマンドが含まれている場合は、追加、`Microsoft.VisualStudio.Assembly`の下の要素、`Assets`要素。 VSIX パッケージ内の SharePoint コマンドを実装するアセンブリの相対パスに新しい要素の値を設定します。 詳細については、次を参照してください。[資産要素 (VSX Schema)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737)します。

    -   拡張機能には、プロジェクトのテンプレートや項目テンプレートが含まれている場合は、追加、`ProjectTemplate`または`ItemTemplate`の下の要素、`Assets`要素。 VSIX パッケージ内のテンプレートが含まれるフォルダーの相対パスに新しい要素の値を設定します。 詳細については、次を参照してください。 [ProjectTemplate 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1)と[ItemTemplate の要素 (VSX Schema)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0)します。

    -   拡張機能には、プロジェクトのテンプレートや項目テンプレートのカスタム ウィザードが含まれている場合は、追加、`Assembly`の下の要素、`Assets`要素。 VSIX パッケージ内のアセンブリの相対パスに新しい要素の値を設定し、設定、`AssemblyName`属性 (バージョン、カルチャ、および公開キー トークンを含む) 完全なアセンブリ名にします。 詳細については、次を参照してください。 [Dependency 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/1f63f60a-98ad-48ec-8e44-4eba383d3e37)します。

### <a name="example"></a>例

次の例では、SharePoint ツール拡張機能の extension.vsixmanifest ファイルの内容を示します。 拡張機能は、Contoso.ProjectExtension.dll というアセンブリに実装されます。 拡張機能には、Contoso.ExtensionCommands.dll とという名前のフォルダーの下の項目テンプレートに指定される SharePoint コマンド アセンブリが含まれています。 **ItemTemplates** VSIX パッケージにします。 この例では、VSIX パッケージに extension.vsixmanifest ファイルと同じフォルダーには、アセンブリの両方を前提としています。

```xml
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />
    <DisplayName>CustomActionProjectItem</DisplayName>
    <Description>Empty VSIX Project.</Description>
  </Metadata>
  <Installation>
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>関連項目

- [SharePoint プロジェクト システムを拡張します。](../sharepoint/extending-the-sharepoint-project-system.md)
- [サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Visual Studio の SharePoint ツールの拡張機能をデバッグします。](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
