---
title: Visual Studio での SharePoint ツールの拡張機能の配置 |Microsoft ドキュメント
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
ms.openlocfilehash: a7ed6b037d04e867b2d94a28fef5ecb6760e39dc
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2018
---
# <a name="deploying-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Visual Studio での SharePoint ツールの拡張機能の配置
  SharePoint ツール拡張機能を展開するには、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]拡張機能のアセンブリおよび拡張機能を配布するその他のファイルを含む拡張機能 (VSIX) パッケージ。 VSIX パッケージは、Open Packaging Conventions (OPC) 標準に準拠した圧縮ファイルです。 VSIX パッケージでは、.vsix 拡張子が付いています。  
  
 VSIX パッケージを作成した後、他のユーザーは、拡張機能のインストールを探し、.vsix ファイルを実行できます。 ユーザーが、拡張機能をインストールすると、%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions フォルダーにすべてのファイル インストールされます。 VSIX パッケージをアップロードする、拡張機能を展開する、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイト、またはすることができます、パッケージ顧客に配布のパッケージをネットワーク共有またはその他のいくつかの Web サイトをホストしているなど、他の方法でします。  
  
 VSIX パッケージの作成と展開の詳細については、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847)を参照してください[Visual Studio 拡張機能の配布](/visualstudio/extensibility/shipping-visual-studio-extensions)です。  
  
 使用して VSIX パッケージを作成することができます、 **VSIX プロジェクト**には、Visual Studio は、テンプレートでは、VSIX パッケージを手動で作成することができます。  
  
## <a name="using-vsix-projects-to-create-vsix-packages"></a>VSIX プロジェクトを使用して VSIX パッケージを作成するには  
 使用することができます、 **VSIX プロジェクト**SharePoint ツールの拡張機能の VSIX パッケージを作成する Visual Studio SDK で提供されるテンプレートです。 VSIX プロジェクトを使用すると、VSIX パッケージを手動で作成するのにいくつかの利点があります。  
  
-   Visual Studio は、プロジェクトをビルドするときに、VSIX パッケージを自動的に生成されます。 配置のファイルをパッケージに追加し、パッケージの [Content_Types] .xml ファイルを作成するなどのタスクが自動的に実行します。  
  
-   VSIX パッケージ内のプロジェクト テンプレートと項目テンプレートなど、他のファイルと、拡張機能プロジェクトのビルド出力を含める VSIX プロジェクトを構成することができます。  
  
 詳細については、VSIX プロジェクトを使用して、次を参照してください。 [VSIX プロジェクト テンプレート](/visualstudio/extensibility/vsix-project-template)です。  
  
### <a name="organizing-your-projects"></a>プロジェクトの整理  
 既定では、VSIX プロジェクトは、アセンブリではないの VSIX パッケージを生成するだけです。 そのため、通常を実装していない SharePoint ツール拡張機能で VSIX プロジェクト。 一般に、少なくとも 2 つのプロジェクトで作業します。  
  
-   VSIX プロジェクト。  
  
-   拡張機能を実装するクラス ライブラリ プロジェクト。  
  
 使用可能な他のプロジェクト特定の種類の拡張機能。  
  
-   拡張機能によって使用されている SharePoint コマンドを実装するクラス ライブラリ プロジェクト。 このシナリオを実証するチュートリアルでは、次を参照してください。[チュートリアル: サーバー エクスプ ローラー Web パーツの表示を拡張する](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)です。  
  
-   項目テンプレート プロジェクトまたはプロジェクト テンプレート プロジェクト拡張機能には、新しい種類の SharePoint プロジェクト項目が定義されている場合、項目テンプレート、またはプロジェクト テンプレートを作成します。 このシナリオを実証するチュートリアルでは、次を参照してください。[チュートリアル: 項目テンプレート、第 1 部にカスタム動作プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)です。  
  
-   拡張機能には、テンプレートが含まれている場合、項目テンプレート、またはプロジェクト テンプレートのカスタム ウィザードを実装するクラス ライブラリ プロジェクト。 このシナリオを実証するチュートリアルでは、次を参照してください。[チュートリアル: 項目テンプレート、第 2 部にカスタム動作プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)です。  
  
 場合は、同じ Visual Studio ソリューション内のすべてのプロジェクトを含めると、クラス ライブラリ プロジェクトのビルド出力を含む VSIX プロジェクトの source.extension.vsixmanifest ファイルを変更できます。  
  
### <a name="editing-the-vsix-manifest"></a>VSIX マニフェストの編集  
 拡張機能に追加するすべてのアイテムのエントリを含めるに VSIX プロジェクトの source.extension.vsixmanifest ファイルを編集する必要があります。 Source.extension.vsixmanifest ファイルを開くには、ショートカット メニューから、ファイル内の XML を編集するための UI を提供する、デザイナーで、ファイルが表示されます。 詳細については、次を参照してください。 [VSIX マニフェスト デザイナー](/visualstudio/extensibility/vsix-manifest-designer)です。  
  
 次の項目の source.extension.vsixmanifest ファイルにエントリを追加する必要があります。  
  
-   拡張機能のアセンブリ。  
  
-   拡張機能によって使用されている SharePoint コマンドを実装するアセンブリ。  
  
-   任意のプロジェクト テンプレートまたは項目テンプレート拡張機能に関連付けられています。  
  
-   拡張機能に関連付けられているテンプレートのカスタム ウィザード。  
  
 次の手順では、これらの各項目の .vsixmanifest ファイルにエントリを追加する方法について説明します。  
  
##### <a name="to-include-the-extension-assembly"></a>拡張機能のアセンブリを含める  
  
1.  VSIX プロジェクトの source.extension.vsixmanifest ファイルのショートカット メニューを開き、クリックして**開く**です。  
  
     ファイルは、デザイナーで開きます  
  
2.  **資産** タブ、エディターの選択、**新規**ボタンをクリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
3.  **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**です。  
  
4.  **ソース**一覧で、次の手順のいずれかを実行します。  
  
    -   拡張機能アセンブリを VSIX プロジェクトと同じソリューション内にあるプロジェクトからビルドする場合は、選択**現在のソリューション内のプロジェクト**です。 **プロジェクト**一覧で、プロジェクトの名前を選択します。  
  
    -   拡張機能のアセンブリがプロジェクト内のファイルとして含まれている場合は選択**ファイルシステム上のファイル**です。 **パス**を一覧表示拡張機能アセンブリ ファイルを完全なパスを入力するかを使用して、**参照**を探して、アセンブリ ファイルを選択してボタンをクリックします。  
  
5.  **[OK]** を選択します。  
  
##### <a name="to-include-a-sharepoint-command-assembly"></a>SharePoint コマンドのアセンブリを含める  
  
1.  VSIX プロジェクトの source.extension.vsixmanifest ファイルのショートカット メニューを開き、クリックして、**開く**ボタンをクリックします。  
  
     このファイルは、デザイナーで開きます。  
  
2.  **資産**セクションで、エディターの選択、**新規**ボタンをクリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
3.  **型**ボックスに、入力**SharePoint.Commands.v4**です。  
  
4.  **ソース**一覧で、次の手順のいずれかを実行します。  
  
    -   コマンド アセンブリを VSIX プロジェクトと同じソリューション内にあるプロジェクトからビルドする場合は、選択**現在のソリューション内のプロジェクト**です。 **プロジェクト**一覧で、プロジェクトの名前を選択します。  
  
    -   コマンド アセンブリがプロジェクト内のファイルとして含まれている場合は選択**ファイルシステム上のファイル**です。 **パス**を一覧表示拡張機能アセンブリ ファイルを完全なパスを入力するかを使用して、**参照**を探して、アセンブリ ファイルを選択してボタンをクリックします。  
  
5.  **[OK]** を選択します。  
  
##### <a name="to-include-a-template-that-you-create"></a>作成したテンプレートを含める  
  
1.  VSIX プロジェクトの source.extension.vsixmanifest ファイルのショートカット メニューを開き、クリックして、**開く**ボタンをクリックします。  
  
     このファイルは、デザイナーで開きます。  
  
2.  **資産**セクションで、エディターの選択、**新規**ボタンをクリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
3.  **型**一覧で、選択 **[microsoft.visualstudio.projecttemplate]** または **[microsoft.visualstudio.itemtemplate]** です。  
  
4.  **ソース**一覧で、選択**現在のソリューション内のプロジェクト**です。  
  
5.  **プロジェクト**ボックスの一覧で、プロジェクトの名前を選択し、、 **OK**ボタンをクリックします。  
  
6.  **ソリューション エクスプ ローラー**プロジェクト テンプレートや項目テンプレート プロジェクトのショートカット メニューを開きを選択し、**プロジェクトのアンロード**です。  
  
7.  クリックして、もう一度、プロジェクト ノードのショートカット メニューを開き**編集***YourTemplateProjectName***.csproj**または**編集***YourTemplateProjectName***です。vbproj**です。  
  
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
  
     `OutputSubPath` 要素は、プロジェクトをビルドするとプロジェクト テンプレートが作成されるパス内の追加フォルダーを指定します。 ここで指定したフォルダーは、顧客が開いたときにだけ、項目テンプレートが使用できることを確認してください、**新しいプロジェクトの追加** ダイアログ ボックスで、展開、 **SharePoint**  ノードを選択し、 **2010。** ノード。  
  
10. ファイルを保存して閉じます。  
  
11. **ソリューション エクスプ ローラー**プロジェクト テンプレートや項目テンプレートのプロジェクトのショートカット メニューを開きを選択し、**プロジェクトの再読み込み**です。  
  
##### <a name="to-include-a-template-that-you-create-manually"></a>手動で作成したテンプレートを含める  
  
1.  VSIX プロジェクトでは、テンプレートを含むようにプロジェクトを新しいフォルダーを追加します。  
  
2.  この新しいフォルダーの下で、次のサブフォルダーを作成しするテンプレート (.zip) ファイルを追加、*ロケール ID*フォルダーです。  
  
     *YourTemplateFolder*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *ロケール ID*  
  
     *YourTemplateName*.zip  
  
     たとえば、英語 (米国) ロケールをサポートする ContosoCustomAction.zip をという名前の項目テンプレートを使っている場合、完全なパスがあります ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip。  
  
3.  **ソリューション エクスプ ローラー**、テンプレート ファイルを選択します (*YourTemplateName*.zip)。  
  
4.  **プロパティ**ウィンドウで、設定、**ビルド アクション**プロパティを**コンテンツ**です。  
  
5.  Source.extension.vsixmanifest ファイルのショートカット メニューを開き、選択**開く**です。  
  
     このファイルは、デザイナーで開きます。  
  
6.  **資産**セクションで、エディターの選択、**新規**ボタンをクリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
7.  **型**一覧で、選択 **[microsoft.visualstudio.itemtemplate]** または **[microsoft.visualstudio.projecttemplate]** です。  
  
8.  **ソース**一覧で、選択**ファイルシステム上のファイル**です。  
  
9. **パス**フィールドに、アセンブリへの完全なパスを入力してください (たとえば、 **ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip**を使用して、または、 **を参照**を見つけて、アセンブリを選択してボタンをクリックしを選択し、 **OK**ボタンをクリックします。  
  
##### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>プロジェクト テンプレートや項目テンプレートのウィザードを含める  
  
1.  VSIX プロジェクトの source.extension.vsixmanifest ファイルのショートカット メニューを開き、クリックして**開く**です。  
  
     このファイルは、デザイナーで開きます。  
  
2.  **資産**セクションで、エディターの選択、**新規**ボタンをクリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
3.  **型**一覧で、選択 **[microsoft.visualstudio.assembly]** です。  
  
4.  **ソース**一覧で、次の手順のいずれかを実行します。  
  
    -   ウィザード アセンブリを VSIX プロジェクトと同じソリューション内にあるプロジェクトからビルドする場合は、選択**現在のソリューション内のプロジェクト**です。 **プロジェクト**一覧で、プロジェクトの名前を選択します。  
  
    -   ウィザード アセンブリがプロジェクト内のファイルとして含まれている場合は選択**ファイルシステム上のファイル**です。 **パス**フィールドは、アセンブリ ファイルを完全なパスを入力するかを使用して、**参照**を見つけて、アセンブリを選択してボタンをクリックします。  
  
5.  **[OK]** を選択します。  
  
### <a name="related-walkthroughs"></a>関連するチュートリアル  
 次の表は、VSIX プロジェクトを使用して、さまざまな種類の SharePoint ツール拡張機能を展開する方法について説明するチュートリアルを一覧表示します。  
  
|拡張機能の種類|関連するチュートリアル|  
|--------------------|--------------------------|  
|拡張機能のアセンブリのみを含む拡張機能|[チュートリアル: SharePoint プロジェクト項目の種類の拡張](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [チュートリアル: SharePoint プロジェクトの拡張機能の作成](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [チュートリアル: サーバー エクスプローラーの拡張機能から SharePoint クライアント オブジェクト モデルを呼び出す](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|SharePoint コマンドを含む拡張機能|[チュートリアル: SharePoint プロジェクトに対するカスタムの配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [チュートリアル: サーバー エクスプローラーを拡張して Web パーツを表示する](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 (パート 2)](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|Visual Studio のテンプレートを含む拡張機能|[チュートリアル: 項目テンプレートに基づくカスタム動作プロジェクト項目の作成 (パート 1)](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 (パート 1)](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|テンプレート ウィザードを含む拡張機能|[チュートリアル: 項目テンプレートに基づくカスタム動作プロジェクト項目の作成 (パート 2)](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 (パート 2)](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## <a name="creating-vsix-packages-manually"></a>VSIX パッケージを手動で作成します。  
 SharePoint ツール拡張機能の VSIX パッケージを手動で作成する場合は、次の手順に従います。  
  
1.  新しいフォルダーになる extension.vsixmanifest ファイルと [Content_Types] .xml ファイルを作成します。 詳細については、次を参照してください。 [VSIX パッケージの構造は](/visualstudio/extensibility/anatomy-of-a-vsix-package)します。  
  
2.  Windows エクスプローラで、2 つの XML ファイルを含むフォルダーを右クリックし、クリックを送信すると、および [圧縮 (zip 形式) フォルダー] をクリックします。 Filename.vsix、ファイル名は、パッケージをインストールする再頒布可能ファイルの名前を指定する、結果として得られる .zip ファイルの名前を変更します。  
  
3.  VSIX パッケージに、拡張機能アセンブリを追加します。 拡張機能には、SharePoint コマンドが含まれている場合は、VSIX パッケージへの SharePoint コマンドを実装するアセンブリも追加します。  
  
4.  Extension.vsixmanifest ファイルを変更します。  
  
    -   追加、`Microsoft.VisualStudio.MefComponent`要素の下、`Assets`要素、および、VSIX パッケージで、拡張機能を実装するアセンブリの相対パスに新しい要素の値を設定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)です。  
  
    -   拡張機能には、SharePoint のサーバー オブジェクト モデルを呼び出す SharePoint コマンドが含まれている場合は、追加、`Microsoft.VisualStudio.Assembly`要素の下、`Assets`要素。 VSIX パッケージ内の SharePoint コマンドを実装するアセンブリの相対パスに新しい要素の値を設定します。 詳細については、次を参照してください。[資産要素 (VSX Schema)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737)です。  
  
    -   拡張機能には、プロジェクト テンプレートや項目テンプレートが含まれている場合は、追加、`ProjectTemplate`または`ItemTemplate`要素の下、`Assets`要素。 VSIX パッケージにテンプレートを含むフォルダーの相対パスに新しい要素の値を設定します。 詳細については、次を参照してください。 [ProjectTemplate 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1)と[ItemTemplate 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0)です。  
  
    -   拡張機能には、カスタム ウィザード プロジェクト テンプレートまたは項目テンプレートが含まれている場合は、追加、`Assembly`要素の下、`Assets`要素。 VSIX パッケージ内のアセンブリの相対パスに新しい要素の値を設定し、設定、`AssemblyName`属性 (バージョン、カルチャ、公開キー トークンを含む) 完全なアセンブリ名にします。 詳細については、次を参照してください。 [Dependency 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/1f63f60a-98ad-48ec-8e44-4eba383d3e37)です。  
  
### <a name="example"></a>例  
 次の例では、SharePoint ツール拡張機能に extension.vsixmanifest ファイルの内容を示します。 拡張機能は、Contoso.ProjectExtension.dll というアセンブリに実装されます。 拡張機能には、Contoso.ExtensionCommands.dll と項目テンプレートをという名前のフォルダーの下に指定される SharePoint コマンド アセンブリが含まれています。**項目テンプレート**VSIX パッケージにします。 この例では、VSIX パッケージ内になる extension.vsixmanifest ファイルと同じフォルダーには、アセンブリの両方を前提としています。  
  
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
 [SharePoint プロジェクト システムの拡張](../sharepoint/extending-the-sharepoint-project-system.md)   
 [サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [SharePoint オブジェクト モデルの呼び出し](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Visual Studio での SharePoint ツールの拡張機能のデバッグ](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  