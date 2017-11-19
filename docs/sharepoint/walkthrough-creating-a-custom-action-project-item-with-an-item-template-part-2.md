---
title: "チュートリアル: 項目テンプレートにカスタム動作プロジェクト項目の作成、パート 2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: 2d8165d3-4af9-4a5e-bdba-8b2a06b1dc8d
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b12a52101feebcfac08c7672834d9d7c65d41c55
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2"></a>チュートリアル: 項目テンプレートに基づくカスタム動作プロジェクト項目の作成 (パート 2)
  SharePoint プロジェクト項目の種類のカスタム定義し、Visual Studio で項目テンプレートに関連付ける、テンプレートのウィザードを提供することがもできます。 ウィザードを使用すると、プロジェクトにプロジェクト項目の新しいインスタンスを追加するのに、テンプレートを使用するときに、ユーザーから情報を収集します。 収集した情報を使用して、プロジェクト項目を初期化できます。  
  
 このチュートリアルで例示されているカスタム動作プロジェクト項目に、ウィザードを追加します[チュートリアル: 項目テンプレート、第 1 部にカスタム動作プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)です。 ウィザードが (その場所と、エンドユーザーが選択すると移動先の URL) などのカスタム アクションに関する情報を収集するユーザーは、SharePoint プロジェクトにカスタム動作プロジェクト項目を追加するときに、新しい Elements.xml ファイルにこの情報を追加プロジェクト項目です。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   カスタム SharePoint プロジェクト項目の種類の項目テンプレートに関連付けられているウィザードを作成します。  
  
-   カスタム ウィザードの Visual Studio での SharePoint プロジェクト項目用の組み込みウィザードのような UI を定義します。  
  
-   置き換え可能パラメーターを使用して、ウィザードで収集したデータで SharePoint プロジェクト ファイルを初期化します。  
  
-   ウィザードをデバッグおよびテストします。  
  
> [!NOTE]  
>  完成したプロジェクト、コード、およびこのチュートリアルでは、次の場所から他のファイルを含むサンプルをダウンロードすることができます:[プロジェクト ファイルを SharePoint ツール拡張機能のチュートリアルについて](http://go.microsoft.com/fwlink/?LinkId=191369)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行する必要があります最初に作成する、CustomActionProjectItem ソリューションを完了して[チュートリアル: 項目テンプレート、第 1 部にカスタム動作プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)です。  
  
 また、このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   サポート対象エディションの Windows、SharePoint、Visual Studio。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   Visual Studio SDK。 このチュートリアルでは、 **VSIX プロジェクト**sdk をプロジェクト項目を配置するための VSIX パッケージを作成するテンプレートです。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツール拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)です。  
  
 次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   Visual Studio のプロジェクトおよび項目テンプレート用のウィザード。 詳細については、次を参照してください。[する方法: プロジェクト テンプレートを使用してウィザードの使用](../extensibility/how-to-use-wizards-with-project-templates.md)と<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>インターフェイスです。  
  
-   SharePoint のカスタム動作。 詳細については、次を参照してください。[カスタム アクション](http://go.microsoft.com/fwlink/?LinkId=177800)です。  
  
## <a name="creating-the-wizard-project"></a>ウィザード プロジェクトの作成  
 このチュートリアルを完了する、CustomActionProjectItem ソリューションで作成したプロジェクトを追加する必要があります[チュートリアル: 項目テンプレート、第 1 部にカスタム動作プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)です。 このプロジェクトで、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスを実装し、ウィザードの UI を定義します。  
  
#### <a name="to-create-the-wizard-project"></a>ウィザード プロジェクトを作成するには  
  
1.  Visual Studio で、CustomActionProjectItem ソリューションを開く  
  
2.  **ソリューション エクスプ ローラー**でソリューション ノードのショートカット メニューを開き、**追加**を選択し**新しいプロジェクト**です。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**または**Visual Basic** 、ノードを選択し、 **Windows**ノード。  
  
4.  上部にある、**新しいプロジェクト** ダイアログ ボックスで、ことを確認して**.NET Framework 4.5** .NET Framework のバージョンの一覧でを選択します。  
  
5.  選択、 **WPF ユーザー コントロール ライブラリ**プロジェクト テンプレートをプロジェクトに名前を**ItemTemplateWizard**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]追加、 **ItemTemplateWizard**プロジェクトがソリューションにします。  
  
6.  プロジェクトから UserControl1 項目を削除します。  
  
## <a name="configuring-the-wizard-project"></a>ウィザード プロジェクトの構成  
 ウィザードを作成する前に、Windows Presentation Foundation (WPF) ウィンドウ、コード ファイル、およびアセンブリ参照をプロジェクトを追加する必要があります。  
  
#### <a name="to-configure-the-wizard-project"></a>ウィザード プロジェクトを構成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ItemTemplateWizard**プロジェクト ノードをクリックして**プロパティ**です。  
  
2.  **プロジェクト デザイナー**、ターゲット フレームワークが .NET Framework 4.5 に設定されていることを確認してください。  
  
     Visual c# プロジェクトの場合にこの値を設定することができます、**アプリケーション**タブです。Visual Basic プロジェクトでこの値を設定することができます、**コンパイル**タブです。詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../ide/how-to-target-a-version-of-the-dotnet-framework.md)」を参照してください。  
  
3.  **ItemTemplateWizard**プロジェクトに追加、**ウィンドウ (WPF)**をプロジェクトに項目をクリックし、項目を名**WizardWindow**です。  
  
4.  CustomActionWizard と文字列の名前の 2 つのコード ファイルを追加します。  
  
5.  ショートカット メニューを開き、 **ItemTemplateWizard**プロジェクトをクリックして**参照の追加**です。  
  
6.  **参照マネージャー - ItemTemplateWizard**ダイアログ ボックスで、**アセンブリ** ノードを選択、**拡張**ノード。  
  
7.  次のアセンブリの横にあるチェック ボックスをオンにして、 **OK**ボタン。  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  **ソリューション エクスプ ローラー**で、**参照**ItemTemplateWizard プロジェクトのフォルダーを選択して、 **EnvDTE**参照します。  
  
9. **プロパティ** ウィンドウの値を変更、**相互運用機能型の埋め込み**プロパティを**False**です。  
  
## <a name="defining-the-default-location-and-id-strings-for-custom-actions"></a>カスタム アクションの ID 文字列と既定の場所を定義します。  
 すべてのカスタム アクションには、場所とで指定されている ID、`GroupID`と`Location`の属性、 `CustomAction` Elements.xml ファイル内の要素。 このステップで ItemTemplateWizard プロジェクトでこれらの属性の有効な文字列の一部を定義します。 このチュートリアルを完了したときに、これらの文字列は、ユーザー、ウィザードで、場所と ID を指定するときに、カスタム動作プロジェクト項目の Elements.xml ファイルに書き込まれます。  
  
 わかりやすくするため、このサンプルでは、使用可能な既定の場所と Id のサブセットのみをサポートしています。 一覧については、次を参照してください。[カスタム アクションの既定の場所と Id](http://go.microsoft.com/fwlink/?LinkId=181964)です。  
  
#### <a name="to-define-the-default-location-and-id-strings"></a>既定の場所と ID の文字列を定義するには  
  
1.  開きます。  
  
2.  **ItemTemplateWizard**プロジェクトで、文字列のコード ファイル内のコードを次のコードに置き換えます。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]  
  
## <a name="creating-the-wizard-ui"></a>ウィザードの UI の作成  
 ウィザードの UI を定義する XAML を追加し、ウィザード内の一部のコントロール ID の文字列にバインドするコードを追加します。 作成するウィザードは、Visual Studio の SharePoint プロジェクト用の組み込みウィザードに似ています。  
  
#### <a name="to-create-the-wizard-ui"></a>ウィザードの UI を作成するには  
  
1.  **ItemTemplateWizard**プロジェクトで、ショートカット メニューを開き、 **WizardWindow.xaml**ファイルをクリックして**開く**デザイナーでウィンドウを開きます。  
  
2.  XAML ビューで、現在の XAML を次の XAML に置き換えます。 XAML では、見出しが含まれています、カスタム動作、およびウィンドウの下部にあるナビゲーション ボタンの動作を指定するコントロールの UI を定義します。  
  
    > [!NOTE]  
    >  このコードを追加した後、プロジェクトはコンパイル エラーの一部になります。 これらのエラーは、この後の手順でコードを追加すると解消されます。  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  この XAML で作成されるウィンドウがから派生した、<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>基本クラスです。 Visual Studio にカスタムの WPF ダイアログ ボックスを追加すると、Visual Studio での他のダイアログ ボックスと一貫したスタイルとをモーダル ダイアログ ボックスで発生する可能性のある問題を回避するのには、このクラスから、ダイアログ ボックスを派生させることをお勧めします。 詳細については、次を参照してください。[モーダル ダイアログ ボックスの管理の作成と](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes)です。  
  
3.  Visual Basic プロジェクトを開発している場合は、削除、`ItemTemplateWizard`から名前空間、`WizardWindow`内のクラス名、`x:Class`の属性、`Window`要素。 この要素は XAML の 1 行目にあります。 完了したら、最初の行は、次のコードをようになります。  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  WizardWindow.xaml ファイルの分離コード ファイルでは、現在のコードを次のコードで置き換えます。  
  
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]  
  
## <a name="implementing-the-wizard"></a>ウィザードの実装  
 実装することによって、ウィザードの機能を定義、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>インターフェイスです。  
  
#### <a name="to-implement-the-wizard"></a>ウィザードを実装するには  
  
1.  **ItemTemplateWizard**プロジェクトを開き、 **CustomActionWizard**コード ファイル、および、このファイルの現在のコードを次のコードに置き換えます。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この段階で、ウィザードに必要なすべてのコードがプロジェクトに揃ったことになります。 エラーが発生することなくプロジェクトをコンパイルできるかどうか、プロジェクトをビルドして確認してください。  
  
#### <a name="to-build-your-project"></a>プロジェクトをビルドするには  
  
1.  メニュー バーの **[ビルド]**、 **[ソリューションのビルド]**の順にクリックします。  
  
## <a name="associating-the-wizard-with-the-item-template"></a>項目テンプレートと、ウィザードの関連付け  
 これで、ウィザードを実装していることを関連付ける必要があります、**カスタム アクション**3 つの主要な手順を完了して項目テンプレート。  
  
1.  ウィザード アセンブリに厳密な名前で署名します。  
  
2.  ウィザード アセンブリの公開キー トークンを取得します。  
  
3.  .Vstemplate ファイルにウィザード アセンブリへの参照を追加、**カスタム アクション**項目テンプレート。  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>ウィザード アセンブリに厳密な名前で署名するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ItemTemplateWizard**プロジェクト ノードをクリックして**プロパティ**です。  
  
2.  **署名**] タブで、[、**アセンブリに署名**チェック ボックスをオンします。  
  
3.  **厳密な名前キー ファイルを選択して**一覧で、選択**\<新規作成 ...> >**です。  
  
4.  **厳密な名前キーの作成** ダイアログ ボックスをオフ、名前を入力、**キーファイルをパスワードで保護する**チェック ボックスをオンにして、 **ok**ボタンをクリックします。  
  
5.  メニュー バーの **[ビルド]**、 **[ソリューションのビルド]**の順にクリックします。  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>ウィザード アセンブリの公開キー トークンを取得するには  
  
1.  Visual Studio コマンド プロンプト ウィンドウで、次を実行してコマンドを置き換える*PathToWizardAssembly* ItemTemplateWizard 上のプロジェクトで、開発ビルド ItemTemplateWizard.dll アセンブリへの完全パスとコンピューターです。  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     ItemTemplateWizard.dll アセンブリの公開キー トークンは、Visual Studio コマンド プロンプト ウィンドウに書き込まれます。  
  
2.  Visual Studio コマンド プロンプト ウィンドウは開いたままにします。 次の手順を実行する場合は、公開キー トークンを必要があります。  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>.vstemplate ファイルにウィザード アセンブリへの参照を追加するには  
  
1.  **ソリューション エクスプ ローラー**、展開、 **ItemTemplate**プロジェクト ノード、および、ItemTemplate.vstemplate ファイルを開きます。  
  
2.  ファイルの末尾の近くで、次の `WizardExtension` 要素を `</TemplateContent>` タグと `</VSTemplate>` タグの間に追加します。 置換、 *YourToken*の値、`PublicKeyToken`前の手順で取得した公開キー トークンを持つ属性。  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     詳細については、`WizardExtension`要素を参照してください[WizardExtension 要素 &#40;です。Visual Studio テンプレート&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  ファイルを保存して閉じます。  
  
## <a name="adding-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>項目テンプレートの Elements.xml ファイルへの置き換え可能パラメーターの追加  
 ItemTemplate プロジェクトの Elements.xml ファイルに複数の置き換え可能パラメーターを追加します。 これらのパラメーターは、前に定義した `PopulateReplacementDictionary` クラスの `CustomActionWizard` メソッドで初期化されます。 ユーザーは、プロジェクトにカスタム動作プロジェクト項目を追加するときに Visual Studio は自動的にウィザードで指定されている値を持つ新しいプロジェクト項目の Elements.xml ファイルでこれらのパラメーターを置き換えます。  
  
 置き換え可能パラメーターはトークンであり、先頭と末尾にはドル記号 ($) が付いています。 独自の置き換え可能パラメーターを定義するだけでなく、SharePoint プロジェクト システムを定義しを初期化するための組み込みパラメーターを使用できます。 詳細については、次を参照してください。[置き換え可能パラメーター](../sharepoint/replaceable-parameters.md)です。  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>置き換え可能パラメーターを Elements.xml ファイルに追加するには  
  
1.  ItemTemplate プロジェクトの Elements.xml ファイルの内容を次の XML に置き換えます。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     新しい XML の値を変更する、 `Id`、 `GroupId`、 `Location`、 `Description`、および`Url`置き換え可能パラメーターに属性をします。  
  
2.  ファイルを保存して閉じます。  
  
## <a name="adding-the-wizard-to-the-vsix-package"></a>VSIX パッケージへのウィザードの追加  
 VSIX プロジェクトの source.extension.vsixmanifest ファイルでは、プロジェクト項目が含まれる VSIX パッケージと共に配置できるように、ウィザード プロジェクトへの参照を追加します。  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>VSIX パッケージにウィザードを追加するには  
  
1.  **ソリューション エクスプ ローラー**から、ショートカット メニューを開き、 **source.extension.vsixmanifest** CustomActionProjectItem プロジェクトのファイルし、順に選択**開く**を開くにはマニフェスト エディターでファイルです。  
  
2.  マニフェスト エディターで、選択、**資産** タブを選択し、**新規**ボタンをクリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
3.  **型**一覧で、選択**[microsoft.visualstudio.assembly]**です。  
  
4.  **ソース**一覧で、選択**現在のソリューション内のプロジェクト**です。  
  
5.  **プロジェクト**一覧で、選択**ItemTemplateWizard**を選択し、 **OK**ボタンをクリックします。  
  
6.  メニュー バーで、次のように選択します。**ビルド**、**ソリューションのビルド**、し、ソリューションがコンパイル エラーが発生しないことを確認します。  
  
## <a name="testing-the-wizard"></a>ウィザードのテスト  
 これで、ウィザードをテストする準備ができました。 まず、Visual Studio の実験用インスタンスで CustomActionProjectItem ソリューションのデバッグを開始します。 Visual Studio の実験用インスタンスでの SharePoint プロジェクトで、カスタム動作プロジェクト項目のウィザードをテストします。 最後に、SharePoint プロジェクトをビルドして実行し、カスタム動作が正常に機能することを確認します。  
  
#### <a name="to-start-to-debug-the-solution"></a>ソリューションのデバッグを始めるには  
  
1.  管理者の資格情報で Visual Studio を再起動し、CustomActionProjectItem ソリューションを開きます。  
  
2.  ItemTemplateWizard プロジェクトで CustomActionWizard コード ファイルを開くし、コードの最初の行にブレークポイントを追加、`RunStarted`メソッドです。  
  
3.  メニュー バーで、次のように選択します。**デバッグ**、**例外**です。  
  
4.  **例外** ダイアログ ボックスで、ことを確認して、**スロー**と**ユーザーよって処理されない**のチェック ボックスを**Common Language Runtime Exceptions**がクリアされを選択し、 **OK**ボタンをクリックします。  
  
5.  選択して、F5 キーを選択するか、メニュー バーでのデバッグを開始**デバッグ**、**デバッグの開始**です。  
  
     Visual Studio では、%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom アクション プロジェクト Item\1.0 に拡張機能をインストールし、Visual Studio の実験用インスタンスを開始します。 このインスタンスの Visual Studio でプロジェクト項目をテストします。  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Visual Studio でウィザードをテストするには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**です。  
  
2.  展開、 **Visual c#**または**Visual Basic** (言語によっては、項目テンプレートをサポートする) ノードが展開、 **SharePoint**ノード、にして、 **2010**ノード。  
  
3.  プロジェクト テンプレートの一覧で選択**SharePoint 2010 プロジェクト**、プロジェクトに名前を**CustomActionWizardTest**を選択し、 **OK**ボタンをクリックします。  
  
4.  **SharePoint カスタマイズ ウィザード**、デバッグに使用するサイトの URL を入力し、、**完了**ボタンをクリックします。  
  
5.  **ソリューション エクスプ ローラー**でプロジェクト ノードのショートカット メニューを開き、**追加**を選択し**新しい項目の**します。  
  
6.  **新しい項目の追加 - CustomItemWizardTest**  ダイアログ ボックスで、展開、 **SharePoint**  ノードの順に展開し、 **2010**ノード。  
  
7.  プロジェクト項目の一覧で選択、**カスタム アクション**項目をクリックして、**追加**ボタンをクリックします。  
  
8.  Visual Studio のもう一方のインスタンスで、先ほど `RunStarted` メソッドに設定したブレークポイントで、コードが停止していることを確認します。  
  
9. F5 キーを選択して、または、メニュー バーで、プロジェクトのデバッグを続行**デバッグ**、**続行**です。  
  
     SharePoint カスタマイズ ウィザードが表示されます。  
  
10. **場所**、選択、**一覧の編集**オプション ボタンをクリックします。  
  
11. **グループ ID**一覧で、選択**通信**です。  
  
12. **タイトル**ボックスに、入力**SharePoint デベロッパー センター**です。  
  
13. **説明**ボックスに、入力**SharePoint デベロッパー センター web サイトが開きます**です。  
  
14. **URL**ボックスに、入力**http://msdn.microsoft.com/sharepoint/default.aspx**を選択し、**完了**ボタンをクリックします。  
  
     isual Studio という項目の追加**CustomAction1**プロジェクトおよびエディターに Elements.xml ファイルが開きます。 Elements.xml にウィザードで指定した値が含まれることを確認します。  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>SharePoint のカスタム動作をテストするには  
  
1.  Visual Studio の実験用インスタンスの F5 キーを押すか、メニュー バーで、次のように選択します。**デバッグ**、**デバッグの開始**です。  
  
     カスタム アクションをパッケージ化されで指定された SharePoint サイトに配置された、**サイト URL**プロジェクト、および web ブラウザーのプロパティをこのサイトの既定のページを開きます。  
  
    > [!NOTE]  
    >  場合、**スクリプト デバッグが無効** ダイアログ ボックスが表示されたら、選択、**はい**ボタンをクリックします。  
  
2.  SharePoint サイトの一覧領域で、選択、**タスク**リンクします。  
  
     **タスク - すべてのタスク**ページが表示されます。  
  
3.  **リスト ツール** タブを選択して、リボンの**リスト** タブで、、**設定**グループで、選択**一覧の設定**です。  
  
     **一覧の設定**ページが表示されます。  
  
4.  下にある、**通信**選択ページの上部の見出しで、 **SharePoint デベロッパー センター**リンク、ブラウザーが web サイト http://msdn.microsoft.com/sharepoint/ を開くことを確認してください。default.aspx を閉じて、ブラウザー。  
  
## <a name="cleaning-up-the-development-computer"></a>開発コンピューターのクリーンアップ  
 プロジェクト項目のテストが終わったら、プロジェクト項目テンプレートを Visual Studio の実験用インスタンスから削除します。  
  
#### <a name="to-clean-up-the-development-computer"></a>開発コンピューターをクリーンアップするには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで、次のように選択します。**ツール**、**拡張機能と更新プログラム**です。  
  
     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で選択、 **Custom Action Project Item**拡張機能を選択し、**アンインストール**ボタンをクリックします。  
  
3.  ダイアログ ボックスが表示されますが、選択、 **[はい]** 、拡張機能をアンインストールし、選択することを確認するにはボタン、**今すぐ再起動**ボタンをクリックしてアンインストールを完了します。  
  
4.  Visual Studio (実験用インスタンスと、CustomActionProjectItem ソリューションが開いている Visual Studio のインスタンス) の両方のインスタンスを閉じます。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: 項目テンプレート、第 1 部にカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [SharePoint プロジェクト項目の項目テンプレートとプロジェクト テンプレートを作成します。](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Visual Studio テンプレート スキーマ参照](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [方法: プロジェクト テンプレートを使用してウィザードを使用します。](../extensibility/how-to-use-wizards-with-project-templates.md)   
 [カスタム アクションの既定の場所と Id](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  